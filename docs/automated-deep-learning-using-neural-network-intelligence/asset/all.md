   

**Automated Deep Learning**

**Using Neural Network**

**Intelligence**

**Develop and Design PyTorch**

**and TensorFlow Models Using Python**

**Ivan Gridin**

 ***Automated Deep Learning Using Neural Network Intelligence: Develop and Design***

***PyTorch and TensorFlow Models Using Python***

Ivan Gridin

Vilnius, Lithuania

ISBN-13 (pbk): 978-1-4842-8148-2

ISBN-13 (electronic): 978-1-4842-8149-9

[https://doi.org/10.1007/978-1-4842-8149-9](https://doi.org/10.1007/978-1-4842-8149-9)

Copyright © 2022 by Ivan Gridin

This work is subject to copyright. All rights are reserved by the Publisher, whether the whole or part of the material is concerned, specifically the rights of translation, reprinting, reuse of illustrations, recitation, broadcasting, reproduction on microfilms or in any other physical way, and transmission or information storage and retrieval, electronic adaptation, computer software, or by similar or dissimilar methodology now known or hereafter developed.

Trademarked names, logos, and images may appear in this book. Rather than use a trademark symbol with every occurrence of a trademarked name, logo, or image we use the names, logos, and images only in an editorial fashion and to the benefit of the trademark owner, with no intention of infringement of the trademark.

The use in this publication of trade names, trademarks, service marks, and similar terms, even if they are not identified as such, is not to be taken as an expression of opinion as to whether or not they are subject to proprietary rights.

While the advice and information in this book are believed to be true and accurate at the date of publication, neither the authors nor the editors nor the publisher can accept any legal responsibility for any errors or omissions that may be made. The publisher makes no warranty, express or implied, with respect to the material contained herein.

Managing Director, Apress Media LLC: Welmoed Spahr

Acquisitions Editor: Celestin Suresh John

Development Editor: Laura Berendson

Coordinating Editor: Mark Powers

Cover designed by eStudioCalamar

Cover image by Vecteezy (www.vecteezy.com)

Distributed to the book trade worldwide by Apress Media, LLC, 1 New York Plaza, New York, NY 10004, U.S.A. Phone 1-800-SPRINGER, fax (201) 348-4505, e-mail orders-ny@springer-sbm.com, or visit www.

springeronline.com. Apress Media, LLC is a California LLC and the sole member (owner) is Springer Science

\+ Business Media Finance Inc (SSBM Finance Inc). SSBM Finance Inc is a **Delaware** corporation.

For information on translations, please e-mail booktranslations@springernature.com; for reprint, paperback, or audio rights, please e-mail bookpermissions@springernature.com.

Apress titles may be purchased in bulk for academic, corporate, or promotional use. eBook versions and licenses are also available for most titles. For more information, reference our Print and eBook Bulk Sales web page at http://www.apress.com/bulk-sales.

Any source code or other supplementary material referenced by the author in this book is available to readers on GitHub (https://github.com/Apress). For more detailed information, please visit http://www.

apress.com/source-code.

Printed on acid-free paper

 *To Ksenia and Elena*

**Table of Contents**

About the Author ����������������������������������������������������������������������������������������������������� xi About the Technical Reviewer ������������������������������������������������������������������������������� xiii Introduction �������������������������������������������������������������������������������������������������������������xv

[Chapter 1: Introduction to Neural Network Intelligence ������������������������������������������� 1](https://doi.org/10.1007/978-1-4842-8149-9_1)

[What Is Automated Deep Learning? ���������������������������������������������������������������������������������������������� 1](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec1)

[No Free Lunch Theorem ���������������������������������������������������������������������������������������������������������� 3](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec2)

[Injecting New Deep Learning Techniques into Existing Model ������������������������������������������������ 6](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec3)

[Adjusting Model to a New Dataset ������������������������������������������������������������������������������������������ 7](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec4)

[Creating a New Model from Scratch ��������������������������������������������������������������������������������������� 8](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec5)

[Reinventing the Wheel ������������������������������������������������������������������������������������������������������������� 9](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec6)

[Working with Source Code ������������������������������������������������������������������������������������������������������������ 9](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec7)

[Neural Network Intelligence Installation ��������������������������������������������������������������������������������������� 9](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec8)

[Install ������������������������������������������������������������������������������������������������������������������������������������� 10](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec9)

[Docker ����������������������������������������������������������������������������������������������������������������������������������� 11](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec10)

[Search Space, Tuner, and Trial ����������������������������������������������������������������������������������������������� 12](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec11)

[Black-Box Function Optimization ������������������������������������������������������������������������������������������ 13](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec12)

[Web User Interface ���������������������������������������������������������������������������������������������������������������������� 18](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec13)

[Overview Page ����������������������������������������������������������������������������������������������������������������������� 18](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec14)

[Trials Details Page ����������������������������������������������������������������������������������������������������������������� 20](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec15)

[NNI Command Line ���������������������������������������������������������������������������������������������������������������� 24](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec16)

[NNI Experiment Configuration ����������������������������������������������������������������������������������������������� 25](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec17)

[Embedded NNI ����������������������������������������������������������������������������������������������������������������������� 27](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec18)

[Troubleshooting ��������������������������������������������������������������������������������������������������������������������� 28](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec19)

[TensorFlow and PyTorch �������������������������������������������������������������������������������������������������������� 29](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec20)

[Summary ������������������������������������������������������������������������������������������������������������������������������� 30](https://doi.org/10.1007/978-1-4842-8149-9_1#Sec21)

v

Table of ConTenTs

[Chapter 2: Hyperparameter Optimization ��������������������������������������������������������������� 31](https://doi.org/10.1007/978-1-4842-8149-9_2)

[What Is Hyperparameter? ����������������������������������������������������������������������������������������������������������� 31](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec1)

[Layer Hyperparameter ����������������������������������������������������������������������������������������������������������� 35](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec2)

[Training Hyperparameter ������������������������������������������������������������������������������������������������������� 35](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec3)

[Feature Hyperparameter ������������������������������������������������������������������������������������������������������� 36](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec4)

[Design Hyperparameter ��������������������������������������������������������������������������������������������������������� 39](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec5)

[Search Space ������������������������������������������������������������������������������������������������������������������������ 40](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec6)

[choice ������������������������������������������������������������������������������������������������������������������������������������ 41](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec7)

[randomint ������������������������������������������������������������������������������������������������������������������������������ 42](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec8)

[uniform ���������������������������������������������������������������������������������������������������������������������������������� 42](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec9)

[quniform �������������������������������������������������������������������������������������������������������������������������������� 42](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec10)

[loguniform ����������������������������������������������������������������������������������������������������������������������������� 42](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec11)

[qloguniform ��������������������������������������������������������������������������������������������������������������������������� 43](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec12)

[normal ����������������������������������������������������������������������������������������������������������������������������������� 43](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec13)

[qnormal ��������������������������������������������������������������������������������������������������������������������������������� 43](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec14)

[lognormal ������������������������������������������������������������������������������������������������������������������������������ 43](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec15)

[qlognormal ���������������������������������������������������������������������������������������������������������������������������� 43](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec16)

[Tuners ������������������������������������������������������������������������������������������������������������������������������������ 46](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec17)

[Random Search Tuner ����������������������������������������������������������������������������������������������������������� 47](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec18)

[Grid Search Tuner ������������������������������������������������������������������������������������������������������������������ 48](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec19)

[Organizing Experiment ���������������������������������������������������������������������������������������������������������� 48](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec20)

[Optimizing LeNet for MNIST Problem ������������������������������������������������������������������������������������ 52](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec21)

[TensorFlow LeNet Implementation ���������������������������������������������������������������������������������������� 57](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec22)

[PyTorch LeNet Implementation ���������������������������������������������������������������������������������������������� 61](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec23)

[Performing LeNet HPO Experiment ���������������������������������������������������������������������������������������� 66](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec24)

[Upgrading LeNet with ReLU and Dropout ������������������������������������������������������������������������������ 71](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec25)

[TensorFlow LeNet Upgrade Implementation �������������������������������������������������������������������������� 75](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec26)

[PyTorch LeNet Upgrade Implementation ������������������������������������������������������������������������������� 78](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec27)

[Performing LeNet Upgrade HPO Experiment ������������������������������������������������������������������������� 82](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec28)

[From LeNet to AlexNet ����������������������������������������������������������������������������������������������������������� 85](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec29)

vi

Table of ConTenTs

[TensorFlow LeNet Evolution Implementation ������������������������������������������������������������������������ 94](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec30)

[PyTorch LeNet Evolution Implementation ���������������������������������������������������������������������������� 100](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec31)

[Performing LeNet Evolution HPO Experiment ���������������������������������������������������������������������� 107](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec32)

[Summary ����������������������������������������������������������������������������������������������������������������������������� 110](https://doi.org/10.1007/978-1-4842-8149-9_2#Sec33)

[Chapter 3: Hyperparameter Optimization Under Shell ����������������������������������������� 111](https://doi.org/10.1007/978-1-4842-8149-9_3)

[Tuners ��������������������������������������������������������������������������������������������������������������������������������������� 111](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec1)

[Evolution Tuner �������������������������������������������������������������������������������������������������������������������������� 117](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec2)

[Anneal Tuner ����������������������������������������������������������������������������������������������������������������������������� 122](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec3)

[Sequential Model-Based Optimization Tuners �������������������������������������������������������������������������� 128](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec4)

[Tree-Structured Parzen Estimator Tuner ����������������������������������������������������������������������������������� 132](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec5)

[Gaussian Process Tuner ������������������������������������������������������������������������������������������������������������ 138](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec6)

[Which Tuner to Choose? ������������������������������������������������������������������������������������������������������������ 142](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec7)

[Custom Tuner ���������������������������������������������������������������������������������������������������������������������������� 144](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec8)

[Tuner Internals �������������������������������������������������������������������������������������������������������������������������� 144](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec9)

[New Evolution Custom Tuner ���������������������������������������������������������������������������������������������������� 147](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec10)

[Early Stopping ��������������������������������������������������������������������������������������������������������������������� 156](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec11)

[Median Stop ������������������������������������������������������������������������������������������������������������������������ 158](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec12)

[Curve Fitting ������������������������������������������������������������������������������������������������������������������������ 162](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec13)

[Risk to Stop a Good Trial ������������������������������������������������������������������������������������������������������ 163](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec14)

[Searching for Optimal Functional Pipeline and Classical AutoML ��������������������������������������� 164](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec15)

[Problem ������������������������������������������������������������������������������������������������������������������������������� 166](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec16)

[Operators ����������������������������������������������������������������������������������������������������������������������������� 168](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec17)

[Search Space ���������������������������������������������������������������������������������������������������������������������� 171](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec18)

[Model ����������������������������������������������������������������������������������������������������������������������������������� 175](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec19)

[Tuner ������������������������������������������������������������������������������������������������������������������������������������ 177](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec20)

[Experiment �������������������������������������������������������������������������������������������������������������������������� 179](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec21)

[Limits of HPO Applying to Neural Architecture Search �������������������������������������������������������� 183](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec22)

[Hyperparameters for Hyperparameter Optimization ����������������������������������������������������������� 183](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec23)

[Summary ����������������������������������������������������������������������������������������������������������������������������� 184](https://doi.org/10.1007/978-1-4842-8149-9_3#Sec24)

vii

Table of ConTenTs

[Chapter 4: Multi-trial Neural Architecture Search ������������������������������������������������ 185](https://doi.org/10.1007/978-1-4842-8149-9_4)

[Neural Architecture As Data Flow Graph ����������������������������������������������������������������������������������� 186](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec1)

[Neural Architecture Search Using Retiarii (PyTorch) ����������������������������������������������������������������� 187](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec2)

[Introduction to NAS Using Retiarii ��������������������������������������������������������������������������������������� 188](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec3)

[Retiarii Framework �������������������������������������������������������������������������������������������������������������� 196](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec4)

[Base Model �������������������������������������������������������������������������������������������������������������������������� 198](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec5)

[Mutators ������������������������������������������������������������������������������������������������������������������������������ 199](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec6)

[Evaluators ���������������������������������������������������������������������������������������������������������������������������� 214](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec13)

[Exploration Strategies ��������������������������������������������������������������������������������������������������������� 215](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec14)

[Experiment �������������������������������������������������������������������������������������������������������������������������� 220](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec20)

[CIFAR-10 LeNet NAS ������������������������������������������������������������������������������������������������������������ 221](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec21)

[CIFAR-10 ResNet NAS ���������������������������������������������������������������������������������������������������������� 236](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec22)

[Classic Neural Architecture Search (TensorFlow) ��������������������������������������������������������������������� 246](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec23)

[Base Model �������������������������������������������������������������������������������������������������������������������������� 247](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec24)

[Mutators ������������������������������������������������������������������������������������������������������������������������������ 248](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec25)

[Trial �������������������������������������������������������������������������������������������������������������������������������������� 250](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec26)

[Search Space ���������������������������������������������������������������������������������������������������������������������� 251](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec27)

[Search Strategy ������������������������������������������������������������������������������������������������������������������� 252](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec28)

[Experiment �������������������������������������������������������������������������������������������������������������������������� 252](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec29)

[Summary ����������������������������������������������������������������������������������������������������������������������������� 256](https://doi.org/10.1007/978-1-4842-8149-9_4#Sec30)

[Chapter 5: One-Shot Neural Architecture Search ������������������������������������������������� 257](https://doi.org/10.1007/978-1-4842-8149-9_5)

[One-Shot NAS in Action ������������������������������������������������������������������������������������������������������������ 257](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec1)

[Supernet Architecture ��������������������������������������������������������������������������������������������������������������� 273](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec2)

[One-Shot Algorithms ����������������������������������������������������������������������������������������������������������������� 282](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec3)

[Efficient Neural Architecture Search (ENAS) ����������������������������������������������������������������������������� 282](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec4)

[TensorFlow ENAS Implementation �������������������������������������������������������������������������������������������� 291](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec5)

[PyTorch ENAS Implementation �������������������������������������������������������������������������������������������������� 293](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec6)

[Differentiable Architecture Search (DARTS) ������������������������������������������������������������������������������ 295](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec7)

[GeneralSupernet Solving CIFAR-10 ������������������������������������������������������������������������������������������� 300](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec8)

[Training GeneralSupernet Using TensorFlow and ENAS ������������������������������������������������������������ 303](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec9)

[Training GeneralSupernet Using PyTorch and DARTS ��������������������������������������������������������������� 310](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec10)

viii

Table of ConTenTs

[HPO vs� Multi-trial NAS vs� One-Shot NAS �������������������������������������������������������������������������������� 317](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec11)

[Summary����������������������������������������������������������������������������������������������������������������������������������� 318](https://doi.org/10.1007/978-1-4842-8149-9_5#Sec12)

[Chapter 6: Model Pruning ������������������������������������������������������������������������������������� 319](https://doi.org/10.1007/978-1-4842-8149-9_6)

[What Is Model Pruning? ������������������������������������������������������������������������������������������������������������ 319](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec1)

[LeNet Model Pruning ����������������������������������������������������������������������������������������������������������������� 322](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec2)

[One-Shot Pruners ���������������������������������������������������������������������������������������������������������������������� 329](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec3)

[Pruner Configuration ����������������������������������������������������������������������������������������������������������������� 333](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec4)

[Level Pruner ������������������������������������������������������������������������������������������������������������������������������ 334](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec5)

[FPGM Pruner ����������������������������������������������������������������������������������������������������������������������������� 337](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec6)

[L1Norm and L2Norm Pruners ��������������������������������������������������������������������������������������������������� 340](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec7)

[Iterative Pruners������������������������������������������������������������������������������������������������������������������������ 342](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec8)

[Linear Pruner ���������������������������������������������������������������������������������������������������������������������������� 343](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec9)

[AGP Pruner �������������������������������������������������������������������������������������������������������������������������������� 344](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec10)

[Iterative Pruner Configuration ��������������������������������������������������������������������������������������������������� 345](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec11)

[Iterative Pruning Scenarios ������������������������������������������������������������������������������������������������������� 346](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec12)

[Best Accuracy Under Size Threshold Scenario ������������������������������������������������������������������������� 347](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec13)

[Minimal Size Above Accuracy Threshold Scenario �������������������������������������������������������������������� 351](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec14)

[Summary����������������������������������������������������������������������������������������������������������������������������������� 355](https://doi.org/10.1007/978-1-4842-8149-9_6#Sec15)

[Chapter 7: NNI Recipes ����������������������������������������������������������������������������������������� 357](https://doi.org/10.1007/978-1-4842-8149-9_7)

[Speed Up Trials ������������������������������������������������������������������������������������������������������������������������� 357](https://doi.org/10.1007/978-1-4842-8149-9_7#Sec1)

[Start–Stop–Resume ������������������������������������������������������������������������������������������������������������������ 358](https://doi.org/10.1007/978-1-4842-8149-9_7#Sec2)

[Continue Finished Experiment �������������������������������������������������������������������������������������������������� 359](https://doi.org/10.1007/978-1-4842-8149-9_7#Sec3)

[NNI and TensorBoard ���������������������������������������������������������������������������������������������������������������� 359](https://doi.org/10.1007/978-1-4842-8149-9_7#Sec4)

[Move Experiment to Another Server ����������������������������������������������������������������������������������������� 363](https://doi.org/10.1007/978-1-4842-8149-9_7#Sec5)

[Scaling Experiments ����������������������������������������������������������������������������������������������������������������� 364](https://doi.org/10.1007/978-1-4842-8149-9_7#Sec6)

[Shared Storage ������������������������������������������������������������������������������������������������������������������������� 367](https://doi.org/10.1007/978-1-4842-8149-9_7#Sec7)

[One-Shot NAS with Checkpoints and TensorBoard ������������������������������������������������������������������� 369](https://doi.org/10.1007/978-1-4842-8149-9_7#Sec8)

[Summary����������������������������������������������������������������������������������������������������������������������������������� 377](https://doi.org/10.1007/978-1-4842-8149-9_7#Sec9)

Index ��������������������������������������������������������������������������������������������������������������������� 379

ix

![](index-9_1.png)

**About the Author**

**Ivan Gridin** is a researcher, author, developer, and artificial

intelligence expert who has worked on distributive high-

load systems and implemented different machine learning

approaches in practice. One of the primary areas of his

research is the design and development of predictive time

series models. Ivan has fundamental math skills in random

process theory, time series analysis, machine learning,

reinforcement learning, neural architecture search, and

optimization. He has published books on genetic algorithms

and time series forecasting.

He is a loving husband and father and collector of old math books.

You can learn more about him on LinkedI[n: https://www.linkedin.com/in/survex/](https://www.linkedin.com/in/survex/).

xi

![](index-10_1.png)

**About the Technical Reviewer**

**Andre Ye** is a deep learning researcher and writer

working toward making deep learning more accessible,

understandable, and responsible through technical

communication. He is also a cofounder at Critiq, a machine

learning platform facilitating greater efficiency in the peer-

review process. In his spare time, Andre enjoys keeping up

with current deep learning research, reading up on history

and philosophy, and playing the piano.

xiii

**Introduction**

Machine learning is a big part of our lives in today's world. We cannot even think of a world without machine learning approaches at the moment, and it has already started to take a huge part of our daily activities. Websites, mobile applications, self-driving cars, home devices, and many things surrounding us use machine learning algorithms. The dawn of computing power, especially the graphics processing unit, was accompanied by the practical start of the deep learning implementation. Deep learning studies the design of deep neural networks. This approach shows impressive efficiency and has experienced explosive growth in recent years.

Not surprisingly, the number of tasks to be solved and the need for machine learning specialists are constantly growing. At the same time, the number of routine actions that developers and data scientists execute to solve machine learning problems is increasing.

Meanwhile, researchers developed special techniques to save time and automate the most common machine learning tasks. These techniques were separated into the

special area called automated machine learning, or AutoML. This book focuses on the automated deep learning (AutoDL) area, which studies the automation of deep learning problems. AutoDL considers the issues of creating and designing optimal deep learning models. This approach has been rapidly developed in recent years and, in some cases, can completely automate the solution of typical tasks.

This book is about implementing AutoDL methods using Microsoft Neural Network

Intelligence (NNI). NNI is a Python toolkit that contains the most common and

advanced AutoDL methods: Hyperparameter Optimization (HPO), Neural Architecture

Search (NAS), and Model Compression. NNI supports the most popular deep learning frameworks. This book covers the NNI implementation of various AutoDL techniques using the PyTorch and TensorFlow frameworks.

Сhapter [1](https://doi.org/10.1007/978-1-4842-8149-9_1) focuses on automated deep learning basics and why we should put this approach into practice. We will also install NNI and examine the main basic scenarios for its use. We will learn how to run simple Hello World Experiments and interact with NNI via the command line and WebUI.

In Сhapt[er 2](https://doi.org/10.1007/978-1-4842-8149-9_2), we will move on to the study of the most common AutoDL task –

Hyperparameter Optimization (HPO). We will learn what Hyperparameter Optimization xv

InTroduCTIon

is, what hyperparameters are, and how to organize an NNI HPO experiment using

PyTorch and TensorFlow. We will also construct three kinds of research that will make a historical journey to the origins of deep learning. The first one will help us determine the best LeNet model hyperparameters for the MNIST problem. The second research

integrates a new dropout layer and rectified linear unit (ReLU) activation into the original LeNet model. And the third one will show us how we can evolve the LeNet model in AlexNet using simple HPO techniques.

In Сhapt[er 3](https://doi.org/10.1007/978-1-4842-8149-9_3), we will study NNI's main search algorithms (Tuners), which aim to solve HPO tasks. Here, we will consider the practical application and the description of the following algorithms: Evolution Tuner, Anneal Tuner, and SMBO Tuners.

Chapt[er 3 pr](https://doi.org/10.1007/978-1-4842-8149-9_3)ovides the creation of a custom Tuner and applies it to the classic Shallow AutoML problem – building an optimal pipeline using Scikit methods.

In Chapter [4, w](https://doi.org/10.1007/978-1-4842-8149-9_4)e will begin to research Neural Architecture Search (NAS). NAS is an approach that studies the creation and design of neural networks best suited to solve a specific problem. This chapter covers Multi-trial NAS and its main principles. We'll discuss the NNI Retiari framework, define Model Spaces and Model Mutators, and set up experiments that construct optimal neural networks. Also, this chapter introduces various exploration algorithms that explore Multi-trial NAS Model Space: Regularized Evolution, TPE Strategy, and RL Strategy. Next, we will build LeNet-based and ResNet-based Multi-trial NAS experiments to solve the CIFAR-10 problem.

In Chapter [5, w](https://doi.org/10.1007/978-1-4842-8149-9_5)e move on to One-shot NAS, one of the latest advances in AutoDL. This chapter explains how to construct a Supernet, how to design cell-based neural architectures, and perform Efficient Neural Architecture Search (ENAS) and Differentiable Architecture Search (DARTS) One-shot NAS algorithms.

In Chapter [6, w](https://doi.org/10.1007/978-1-4842-8149-9_6)e will cover the important topic of model pruning. Model pruning compresses neural network removing redundant weights or even layers. This technique is crucial for lightweight devices when we need to save computing resources. This chapter will examine basic One-shot and iterative pruning algorithms.

Chapt[er 7 w](https://doi.org/10.1007/978-1-4842-8149-9_7)ill focus on practical recipes for using NNI to organize robust, extensive, and big data experiments.

This book explores practical NNI applications of AutoDL methods and describes

their theory also. Therefore, this book can be helpful for data scientists who want to get the idea that underlies various AutoDL techniques and algorithms.

This book requires intermediate deep learning understanding and TensorFlow or

PyTorch knowledge.

xvi

InTroduCTIon

**Source Code Listings**

This book has many practical examples and code listings. Source code listings

accompany each chapter in this book. You can download the source code from the

following GitHub repository: [https://github.com/Apress/automated-deep-learning-](https://github.com/Apress/automated-deep-learning-using-neural-network-intelligence)

[using-neural-network-intelligence](https://github.com/Apress/automated-deep-learning-using-neural-network-intelligence).

xvii

**CHAPTER 1**

**Introduction to Neural**

**Network Intelligence**

There was a great burst of deep learning industry in the past few years. Deep learning approaches have achieved outstanding results in computer vision, natural language processing, robotics, time series forecasting, and optimal control theory. However, there is no “silver bullet model” to solve all kinds of problems. Each problem and dataset needs a specific model architecture to achieve suitable performance. Machine learning models, especially deep learning models, have a lot of tunable parameters that can drastically affect the model performance. Those are model design, training method, model configuration hyperparameters, etc. The model optimization process is performed for each application and even each dataset. Data scientists and machine learning experts often spend a lot of time performing manual model optimization. This activity can be frustrating because it takes too much time and is usually based on an expert’s experience and quasi-random search.

However, recent results in automated machine learning and deep learning meta-

optimization make it possible to automate the optimizing process for a specific task.

It is also possible to create brand new model architecture from scratch without having any experience solving similar problems in the past. The Neural Network Intelligence (**NNI**) toolkit provides the latest state-of-the-art techniques to solve the most challenging automated deep learning problems. We’ll start exploring the basic NNI features in this chapter.

**What Is Automated Deep Learning?**

Before we dive into NNI techniques, let’s talk about automated deep learning, examine its use cases, and why you need it. Modern machine learning models can contain

enormous complexity in their design. Architecture can have thousands of adjustable 1

© Ivan Gridin 2022

I. Gridin, *Automated Deep Learning Using Neural Network Intelligence*,

[https://doi.org/10.1007/978-1-4842-8149-9\_1](https://doi.org/10.1007/978-1-4842-8149-9_1#DOI)

![](index-15_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

parameters and connections between different neural layers. It is computationally impossible to test each architecture hyperparameter combination to select the best one. However, modern graphics processing units can already significantly speed up the training of machine and especially deep learning models, which means that many machine learning processes can be automated. Therefore, a new domain in machine

learning has appeared called automated machine learning (**AutoML**). AutoML deals with tasks that automate optimal machine learning model production. The area of

AutoML is very young and is growing rapidly. Machine learning can be divided into shallow learning and deep learning. Shallow learning contains classical methods: random forest, support vector machine, k-nearest neighbors, etc. In comparison, deep learning studies the construction of neural networks based on convolution layers, linear layers, pooling, splitting and joining connections, etc. Shallow learning and deep learning contain similar automated machine learning techniques, but their application differs significantly. Therefore, we can highlight a separate area of AutoML, which deals only with deep learning – this area is called automated deep learning (**AutoDL**). There are four main sections for automated deep learning:

• Hyperparameter Optimization (**HPO**)

• Neural Architecture Search (**NAS**)

• Feature Engineering

• Model Compression

***Figure 1-1.** AutoDL sections*

Let’s move on and discuss what exactly we need AutoDL for.

2

Chapter 1 IntroduCtIon to neural network IntellIgenCe

**No Free Lunch Theorem**

And I want to start with the following fundamental statement, called the No Free Lunch (**NFL**) theorem. No Free Lunch theorem states that

*Any two optimization algorithms are equivalent*

*when their performance is averaged across all possible problems.*

—David Wolpert

Let’s elaborate NFL theorem to more functional language. Say we have a set of

datasets: ***D1***, ***D2***, ***D3***, ..., and the estimated performance of random search algorithm ***R*** on each dataset ***Di*** equals to *r*:

E( ***R***; ***Di***) = *r*, for any *I* (1)

Then for any search algorithm ***A*** and any dataset ***Di*** with estimation *r + q*, there is a dataset ***Dj*** with estimation *r - q*:

E( ***A***; ***D*****i**) = *r* + *q*, E( ***A***; ***D*****j**) = *r* – *q* (2) Statement 2 says that if algorithm ***A*** is better than random algorithm ***R*** for dataset ***Di***, then there is dataset ***Dj*** for which algorithm ***A*** will be worse than random algorithm ***R***

and E( ***A***; ***Di**) +* E *(**A**;* ***Dj**) = E(**R**;* ***Di**) + E(**R**;* ***Dj**)*. This fact makes all algorithms equivalent if we consider them separately from a specific dataset and task. For example, let’s say we have an algorithm ***A*** for predicting the color of the next box by previous ones with rules listed in Table [1-1](#index_split_000.html#p16).

***Table 1-1.** Box prediction algorithm*

**Rule**

**Previous Box**

**Current Box**

**Prediction**

1

Black

Black

white

2

Black

white

white

3

white

Black

Black

4

white

white

Black

3

![](index-17_1.png)

![](index-17_2.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

And the prediction algorithm **A** works with 100% accuracy for dataset **D**1, in which two black boxes follow two white boxes and two white boxes follow two black boxes, as shown in Figure [1-2](#index_split_000.html#p17).

***Figure 1-2.** Performance of prediction algorithm **A** on dataset **D1**: 100% accuracy* But let’s examine how algorithm **A** works on dataset **D2**, in which white and black boxes alternate one after another one by one, as shown in Figur[e 1-3.](#index_split_000.html#p17)

***Figure 1-3.** Performance of prediction algorithm **A** on dataset **D2**: 0% accuracy* 4

![](index-18_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

Figur[e 1-3 demons](#index_split_000.html#p17)trates that algorithm **A** has 0% accuracy on dataset **D2**. This example illustrates that “there is no optimal algorithm for all datasets” and “there is no optimal solution for all cases.” And how does NFL theorem influence deep learning?

Each deep learning model and each dataset generates a loss function that should be minimized. If we have two deep learning models, **M1** and **M2**, then this means that they show good results only for certain types of problems and certain types of datasets. You cannot expect the same deep learning model to perform similarly on a different dataset, much less for a different kind of problem. So if you apply model **M1** and model **M2** to problem **P1** on dataset **D1**, you can expect that model **M1** will show good performance in this case, and model **M2** will demonstrate poor performance. Figur[e 1-4](#index_split_000.html#p18) illustrates this point.

***Figure 1-4.** Performance of model M1 and M2 on dataset D1 for problem P1*

But we can get the opposite results if the models are applied to a different problem and a different dataset as shown in Figur[e 1-5.](#index_split_000.html#p19)

5

![](index-19_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-5.** Performance of model M1 and M2 on dataset D2 for problem P2*

So, the NFL theorem tells us that we cannot expect a model to perform equally well for different cases. The slightest modification in the problem statement or changes in the dataset require additional model optimization for the updates. This fact makes the AutoDL irreplaceable in preparing an effective production-ready solution. It is also worth mentioning that the set of realistic datasets is much smaller than the set of all possible datasets, which makes it possible to determine a class of most suitable algorithms for solving specific problems. Nevertheless, the NFL theorem remains true since selecting the best algorithm for all types of problems is impossible.

**Injecting New Deep Learning Techniques into**

**Existing Model**

Suppose we have a deep learning model that performs well and shows satisfactory

results. Later, a new deep learning technique appeared that could significantly improve the performance of our model. It could be a special deep learning layer, block, cell, or a new activation function. But we do not know how exactly to inject that technique into the model architecture. This can be accomplished with AutoDL, which will make optimal use of the new technique in the current deep learning model design. Figur[e 1-6](#index_split_000.html#p20)

illustrates this approach.

6

![](index-20_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-6.** Injecting new deep learning technique*

This approach will help update the model with the latest advances in deep learning, enhancing the model’s performance.

**Adjusting Model to a New Dataset**

Let’s say we have a model that solves the problem of energy consumption prediction in New York. The model has been trained on the historical dataset and works well. We have decided to port this model for energy consumption prediction in Berlin. We expect this model to perform for Berlin as well as it performed for New York. But people in another country may have a little bit different habits and behaviors that affect the original model’s ability to capture patterns correctly. Therefore, it would be good to customize the original model for the new Berlin historical dataset. Figure [1-7](#index_split_000.html#p21) demonstrates how the existing model could be adapted to a new dataset, updating some of its hyperparameters like convolution layer filters, linear layer features, etc.

7

![](index-21_1.png)

![](index-21_2.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-7.** Adapting model to new dataset*

Using AutoDL techniques, you can adapt the model to other datasets.

**Creating a New Model from Scratch**

And this is the most exciting part. Let’s say we have a task, and there is no idea about the architecture of a neural network that could cope with it. We can borrow some ideas from other tasks, do manual investigations, study the statistical properties of the dataset, etc.

But at the moment, there are Neural Architecture Search (**NAS**) methods that allow you to build a production-ready neural network from scratch, as shown in Figur[e 1-8.](#index_split_000.html#p21)

***Figure 1-8.** Neural Architecture Search*

8

Chapter 1 IntroduCtIon to neural network IntellIgenCe

And I find this to be a fantastic direction for further research and practical

applications. Humanity has developed deep learning models and their training based on error backpropagation. Neural networks of a particular architecture can reveal the most complex dependencies and patterns. So why not take the next step and develop neural network design algorithms that will create the optimal neural network architecture for a specific task.

**Reinventing the Wheel**

Many machine learning experts spend a lot of time developing existing methods to solve the problems described earlier. Automated machine learning techniques can save weeks or even months of development. Of course, automated deep learning cannot substitute for deep learning engineers, and human experience and intuition is the main driver in all inventions nowadays. But anyway, AutoDL can significantly decrease the amount of custom work needed. Automated deep learning should become a must-have tool for

solving practical problems that can save significant time.

**Working with Source Code**

This book demonstrates many practical examples, accompanied by source code that

can be downloaded from the following GitHub repository. This book has many practical examples and code listings. The chapter’s source code listings accompany each chapter in this book. You can download the source code from the following GitHub repository:

[**https://github.com/Apress/automated-deep-learning-using-neural-network-**](https://github.com/Apress/automated-deep-learning-using-neural-network-intelligence)

[**intelligence**](https://github.com/Apress/automated-deep-learning-using-neural-network-intelligence). Most of the listings in the book are presented in source code. All commands in the book are run relative to the root of the source code folder.

**Neural Network Intelligence Installation**

Neural Network Intelligence (**NNI**) is a powerful toolkit to help users solve AutoML. NNI manages search processes, visualizes results, and distributes AutoML jobs to different machine learning platforms.

9

Chapter 1 IntroduCtIon to neural network IntellIgenCe

**Install**

NNI minimal system requirements are: Ubuntu, 18.04; macOS, 11; Windows 10, 21H2

and Python 3.7.

NNI can be simply installed as follows:

pip install nni

We will be using version 2.7 in this book, so I highly recommend installing version 2.7 to avoid version differences:

pip install nni==2.7

Let’s test the installation by executing “*Hello World*” scenario. Run the following command (ch1/install/hello\_world/config.yml file is contained in the source code): nnictl create --config ch1/install/hello\_world/config.yml

If the installation was successful, you should see the following output:

INFO: Starting restful server...

INFO: Successfully started Restful server!

INFO: Starting experiment...

INFO: Successfully started experiment!

The experiment id is <EXPERIMENT\_ID>

The Web UI urls are: http://127.0.0.1:8080

And you can follo[w the link http://127.0.0.1:8080](http://127.0.0.1:8080) in your browser. Figure [1-9](#index_split_000.html#p24)

demonstrates NNI web user interface that we will cover in the next sections.

10

![](index-24_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-9.** NNI WebUI*

If everything is ok, then you can stop NNI by executing the following in the

command line:

nnictl stop

**Docker**

If you have any problems with the installation, you can use the docker image that was prepared for this book. The Dockerfile in Listin[g 1-1 is b](#index_split_000.html#p24)ased on the official NNI docker image msranni/nni:v2.7 from the official docker repository: [https://hub.docker.](https://hub.docker.com/r/msranni/nni/tags)

[com/r/msranni/nni/tags.](https://hub.docker.com/r/msranni/nni/tags)

***Listing 1-1.*** NNI Dockerfile for the book.

FROM msranni/nni:v2.7

RUN mkdir /book

ADD . /book

EXPOSE 8080

ENTRYPOINT \["tail", "-f", "/dev/null"\]

11

Chapter 1 IntroduCtIon to neural network IntellIgenCe

And you can build an image as

docker build -t autodl\_nni\_book .

The docker autodl\_nni\_book image contains all the necessary libraries and

dependencies to run all the experiments that we will study in this book.

Let’s run the “*Hello World*” scenario we examined in the previous section using docker. We start the docker container:

docker run -t -d -p 8080:8080 autodl\_nni\_book

then we run NNI in the docker container:

docker exec <container\_id> bash -c "nnictl create --config

/book/ch1/install/hello\_world/config.yml"

and after that, you can access NNI WebUI vi[a http://127.0.0.1:8080 in y](http://127.0.0.1:8080)our browser.

The code repository for this book is in /book directory of the docker image. Therefore, in the autodl\_nni\_book docker image, you can execute all commands that will concern NNI as follows:

docker exec <container\_id> bash -c "nnictl <nni\_command>"

But in any case, the docker’s capabilities are limited. For flexible debugging and better interaction with NNI, I strongly recommend that you work with NNI without using the docker if possible.

**Search Space, Tuner, and Trial**

Let’s take a quick look at one core NNI concept. When we optimize a model, we select a particular set of parameters that determine the operation of our model. **Search space** defines this set of parameters. Search space is a key concept in automatic machine learning. The search space contains all possible parameters and architectures that are hypothetically acceptable for the optimized model.

Although the search space contains a finite number of parameters, nevertheless in most cases, it is practically impossible to test all parameters from the search space. The search space is too large. Therefore, a special component called **Tuner** is applied in selecting the most appropriate and promising parameters for testing. Tuner estimates the results and selects new parameters to check their suitability for model optimization.

12

![](index-26_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

Tuner selects a parameter in the search space and transfers it to **Trial**. Trial is a Python script that tests the model with parameters passed by Tuner and returns a metric that estimates the model’s performance.

This search process can be depicted as shown in Figur[e 1-10](#index_split_000.html#p26).

***Figure 1-10.** Search space, Tuner, and Trial*

After a certain number of trials, we have a sufficient number of results that estimate the suitability of each parameter for an optimized model.

**Black-Box Function Optimization**

Let’s examine how NNI works by optimizing a black-box function. A black-box function is a function that takes input parameters and returns a value, but we have no idea what is going on under the function’s hood. Sometimes, we know how a black-box function acts and, in some cases, even know its formula. But the nature of this function is so complicated that the analytical study is too challenging.

13

![](index-27_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-11.** Black-box function*

When we say that we need to optimize the black-box function, it means that we

need to find such input parameters for which the black-box function outputs the highest value. Let’s say that we have a black-box function, which is defined by the code in Listin[g 1-2.](#index_split_000.html#p27)

***Listing 1-2.*** Black-box function. ch1/bbf/black\_box\_function.py

from math import sin, cos

def black\_box\_function(x, y, z):

"""

x in \[1, 100\] integer

y in \[1, 10\] integer

z in \[1, 10000\] real

"""

if y % 2 == 0:

if x > 50:

r = (pow(x, sin(z)) - x) \* x / 2

else:

r = (pow(x, cos(z)) + x) \* x

else:

r = pow(y, 2 - sin(x) \* cos(z))

return round(r / 100, 2)

14

Chapter 1 IntroduCtIon to neural network IntellIgenCe

Of course, the optimization problem for the function presented in Listin[g 1-2 c](#index_split_000.html#p27)an be solved analytically, but let’s pretend that we do not know how the function acts inside the black box. All we know is that the black-box function returns real value and receives the following input parameters:

• x positive integer from 1 to 100

• y positive integer from 1 to 10

• z float from 1 to 10 000

Let’s start solving our problem by defining a search space. Search space is defined in JSON format using special directives. We will define the search space using the following JSON file.

***Listing 1-3.*** Search space. ch1/bbf/search\_space.json

{

"x": {"\_type": "quniform", "\_value": \[1, 100, 1\]},

"y": {"\_type": "quniform", "\_value": \[1, 10, 1\]},

"z": {"\_type": "quniform", "\_value": \[1, 10000, 0.01\]}

}

quniform directive creates a value list from a to b with step s. So the search space defined in Listing [1-3](#index_split_000.html#p28) can be presented the following way:

• x in \[1, 2, 3, …, 99, 100\]

• y in \[1, 2, 3, …, 9, 10\]

• z in \[1, 1.01, 1.02, …, 9 999.99, 10 000\]

**Note** we’ll explore how to define search space in more detail in the next chapter.

Now let’s move on to the trial definition.

***Listing 1-4.*** Trial. ch1/bbf/trial.py

import os

import sys

import nni

15

Chapter 1 IntroduCtIon to neural network IntellIgenCe

\# For NNI use relative import for user-defined modules

SCRIPT\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_)) + '/../..'

sys.path.append(SCRIPT\_DIR)

from ch1.bbf.black\_box\_function import black\_box\_function

if \_\_name\_\_ == '\_\_main\_\_':

\# parameter from the search space selected by tuner

p = nni.get\_next\_parameter()

x, y, z = p\['x'\], p\['y'\], p\['z'\]

r = black\_box\_function(x, y, z)

\# returning result to NNI

nni.report\_final\_result(r)

Trial receives parameter from NNI using nni.get\_next\_parameter function and

returns the metric using nni.report\_final\_result. Trial takes NNI parameters, passes them to the black-box function, and returns the result. Listing [1-4](#index_split_000.html#p28) has to be run by the NNI server, so you will get an error if you try to run it.

**Note** we’ll explore how to define trial in more detail in the next chapter.

And the last thing left for us to do is to define the configuration of our experiment, which will look for the best input parameters for the black-box function.

***Listing 1-5.*** Experiment configuration. ch1/bbf/config.yml

trialConcurrency: 4

maxTrialNumber: 1000

searchSpaceFile: search\_space.json

trialCodeDirectory: .

trialCommand: python3 trial.py

tuner:

name: Evolution

classArgs:

optimize\_mode: maximize

trainingService:

platform: local

16

Chapter 1 IntroduCtIon to neural network IntellIgenCe

The experiment that we have defined in Listin[g 1-5 h](#index_split_000.html#p29)as the following properties:

• Four-thread pool for trial execution.

• The maximum number of trials is 1000.

• Search space is defined in search\_space.json.

• Trial is executed by running python3 trial.py.

• NNI will use a Tuner based on genetic algorithms.

**Note** we’ll explore how to define experiment configuration in more detail in the next chapter.

Now everything is ready to find the input parameters that maximize the black-box function. Let’s run NNI:

nnictl create --config ch1/bbf/config.yml

And you can monitor the experiment process in the web panel:

[http://127.0.0.1:8080](http://127.0.0.1:8080).

**Note** typically, testing a deep learning model architecture takes about a few minutes, and the nnI is optimized for longer trials. therefore, the nnI is not well suited for high-speed tests, and executing the value of the black-box function

can take more time than expected. this is due to the data exchange mechanism

between the main nnI process and its sub-processes. If you want to shorten the

experiment execution time, change the maxTrialNumber parameter to 100 in

ch1/bbf/config.yml.

After completing the experiment, you can observe the parameter that returned the best metric on the NNI overview pag[e: http://127.0.0.1:8080/oview](http://127.0.0.1:8080/oview).

17

![](index-31_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-12.** NNI best trial for black-box function optimization*

We see that parameter (x=49, y=2, z=7024.61) is the best result of the experiment.

The function for this parameter returns 48.02, which is the maximum of all trials.

Of course, we could have obtained the same result more simply, but now, we are

introducing the basic capabilities of NNI. In the next chapters, we will see the full strength of this tool.

**Web User Interface**

Even though NNI allows you to save trial results and later analyze them, NNI provides a convenient web user interface for experiment monitoring and analyzing its results. Let’s explore the main features of this web panel.

**Overview Page**

The overview page [http://127.0.0.1:8080/oview](http://127.0.0.1:8080/oview) contains summary information about a running experiment.

The upper left panel contains information about the experiment state (Figur[e 1-13](#index_split_000.html#p32)).

18

![](index-32_1.png)

![](index-32_2.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-13.** Experiment state panel*

The lower left panel shows the number of trials performed and the running time. The maximum number of trials and the maximum time can be edited on the fly (Figur[e 1-14](#index_split_000.html#p32)).

***Figure 1-14.** Trial numbers panel*

The right panel on the overview page contains a summary of the top trials

(Figure [1-15).](#index_split_000.html#p33)

19

![](index-33_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-15.** Top trials panel*

If you just want to run an experiment and get the best test result, then you can only deal with the overview page. But for a more detailed analysis of the experiment execution, you will need the trials details page.

**Trials Details Page**

The trials details pag[e http://127.0.0.1:8080/detail](http://127.0.0.1:8080/detail) contains a handy visualization of the trials performed. The metric panel contains a history of trials and their metrics. This panel becomes very useful if you toggle the optimization curve. Then you can observe the tuner search progress (Figur[e 1-16](#index_split_000.html#p34)).

20

![](index-34_1.png)

![](index-34_2.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-16.** Metric panel*

The hyperparameter panel contains one of the most valuable visualizations. It

displays the relationship between the input parameters and the test metric (Figur[e 1-17).](#index_split_000.html#p34)

***Figure 1-17.** Hyperparameter panel*

This panel allows hyperparameter data mining to help you better understand the

nature of the investigated black-box function. We will stay on this moment for a while.

Select the top 5% trials on the hyperparameter panel (Figure [1-18).](#index_split_000.html#p35)

21

![](index-35_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-18.** Hyper-parameter panel. Top 5%*

And we can get a lot of insights from Figur[e 1-18. F](#index_split_000.html#p35)or all top 5% trials, the following is true:

• x is an integer less than 51, that is, 50, 49, 48.

• y is even.

• z probably does not significantly affect the black-box function return

value, or further research may be needed.

Based on the information we obtained here, we can perform our own simplified

search that finds the best parameter close to 48.02, which was found during the NNI experiment. Let’s examine Listin[g 1-6.](#index_split_000.html#p35)

***Listing 1-6.*** Black-box function optimization. ch1/bbf/custom\_search.py import random

from ch1.bbf.black\_box\_function import black\_box\_function

seed = 0

random.seed(0)

max\_ = -100

best\_trial = None

for \_ in range(100):

x = random.choice(\[50, 49, 48\])

y = random.choice(\[2, 4, 6, 8, 10\])

22

![](index-36_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

z = round(random.uniform(1, 10\_000), 2)

r = black\_box\_function(x, y, z)

if r > max\_:

max\_ = r

best\_trial = f'(x={x}, y={y}, z={z}) -> {r}'

print(best\_trial)

Listin[g 1-6 r](#index_split_000.html#p35)eturns (x = 50, y = 2, z = 4756.58) -> 47.96, which is pretty close to the best value of 48.02 we found in our NNI experiment. The next chapters will demonstrate that examining the hyperparameter panel allows you to comprehend many key concepts of an effective deep learning model.

At the bottom of the page is the Trial list panel, which lists all trials. You can observe each trial’s parameters, logs, and metrics, as shown in Figur[e 1-19](#index_split_000.html#p36).

***Figure 1-19.** Trial list panel*

An experiment is usually a rather lengthy process that can take days or even

weeks. Sometimes, there may be interesting hypotheses to test. For example, it may be necessary to run a trial with specific parameters manually. And if you don’t want to wait until the end of the experiment, then you can add a custom trial to the queue by clicking the “Copy” button in the list of challenges. You can enter your trial parameters in the pop-up window and submit a trial. Figure [1-20 demons](#index_split_000.html#p37)trates how you can submit a custom trial.

23

![](index-37_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Figure 1-20.** Customized trial*

NNI offers a web panel for experiments that simplifies administration and

monitoring tasks. We will get back to it more than once in the next chapters.

**NNI Command Line**

In addition to the web panel, you can use the command-line interface to manage the NNI and monitor its experiments. NNI has the following working directory: ~/nni-experiments, where all data about experiments is stored.

**nnictl create --config <path\_to\_config>** : Starts an experiment and returns

<experiment\_id>. During execution, all information about the running experiment is saved in ~/nni-experiments/<experiment\_id>.

**nnictl stop**: Stops running experiment.

**nnictl experiment list --all**: Returns a list of all created experiments.

**nnictl resume <experiment\_id>** : Resumes a stopped experiment. This command is also useful when you want to analyze the results of an already completed experiment.

**nnictl view <experiment\_id>** : Outputs information about experiment.

24

Chapter 1 IntroduCtIon to neural network IntellIgenCe

**nnictl top**: Outputs best trials.

For more information about NNI command-line tool, please refer to

**nnictl --help**

**NNI Experiment Configuration**

As we saw earlier, the execution of the experiment is configured through a YAML file (ch1/bbf/config.yml). NNI allows you to configure the experiment execution flexibly.

Table [1-2](#index_split_000.html#p38) lists the main configuration parameters.

***Table 1-2.** NNI experiment configuration settings*

**Field**

**Type**

**Description**

experimentName

str

name of the experiment

optional

searchSpaceFile

str

path to the JSon file containing search space

optional

definition

searchSpace

YAML

Field for inline search space definition

optional

For example, search space defined in ch1/

bbf/search\_space.json can be set in

searchSpace field:

searchSpace:

x:

\_type: quniform

\_value: \[1, 100, 1\]

y:

\_type: quniform

\_value: \[1, 10, 1\]

z:

\_type: quniform

\_value: \[1, 10000, 0.01\]

trialCommand

str

Command to execute trial. use python3 on

required

linux and macoS, and use python on windows

( *continued*)

25

Chapter 1 IntroduCtIon to neural network IntellIgenCe

***Table 1-2.*** ( *continued*)

**Field**

**Type**

**Description**

trialCodeDirectory

str

path to trial directory

optional

default: "."

trialConcurrency

int

Number of trials to run concurrently

maxExperimentDuration

str

limits the experiment duration. experiment

optional

duration is not limited by default

Format: number + s|m|h|d

example:

maxExperimentDuration: 5h

maxTrialNumber

int

limits the number of trials. number of trials is

optional

not limited by default

maxTrialDuration

str

limits the trial duration. trial duration is not

optional

limited by default.

Format: number + s|m|h|d

example:

maxTrialDuration: 30m

debug

bool

enables debug mode

optional

default: False

tuner

YAML

Specifies the hyperparameter tuner. details in

optional

*Chapter* [*3*](https://doi.org/10.1007/978-1-4842-8149-9_3)

assessor

YAML

Specifies the assessor. details in *Chapter* [*3*](https://doi.org/10.1007/978-1-4842-8149-9_3)

optional

advisor

YAML

Specifies the advisor. details in *Chapter* [*3*](https://doi.org/10.1007/978-1-4842-8149-9_3)

optional

trainingService

YAML

Specifies the training service. details in *Chapter* [*7*](https://doi.org/10.1007/978-1-4842-8149-9_7)

optional

sharedStorage

YAML

Specifies the shared storage. details in *Chapter* [*7*](https://doi.org/10.1007/978-1-4842-8149-9_7)

optional

26

Chapter 1 IntroduCtIon to neural network IntellIgenCe

For more details, please refer to the official documenta[tion: https://nni.](https://nni.readthedocs.io/en/v2.7/reference/experiment_config.html)

[readthedocs.io/en/v2.7/reference/experiment\_config.html.](https://nni.readthedocs.io/en/v2.7/reference/experiment_config.html)

**Embedded NNI**

Even though the capabilities of the NNI server are quite broad, the NNI can run in embedded mode. It is more convenient to run NNI in Python embedded mode in some

cases. This need may arise when it is necessary to dynamically create experiments and have more control over the experiment execution. We will use NNI in embedded mode in some examples in the next chapters.

Listin[g 1-7 sho](#index_split_000.html#p40)ws an example of the execution of an experiment in embedded mode to optimize the black-box function we examined earlier.

***Listing 1-7.*** Embedded NNI. ch1/bbf/embedded\_nni.py

\# Loading Packages

from pathlib import Path

from nni.experiment import Experiment

\# Defining Search Space

search\_space = {

"x": {"\_type": "quniform", "\_value": \[1, 100, 1\]},

"y": {"\_type": "quniform", "\_value": \[1, 10, 1\]},

"z": {"\_type": "quniform", "\_value": \[1, 10000, 0.01\]}

}

\# Experiment Configuration

experiment = Experiment('local')

experiment.config.experiment\_name = 'Black Box Function Optimization'

experiment.config.trial\_concurrency = 4

experiment.config.max\_trial\_number = 1000

experiment.config.search\_space = search\_space

experiment.config.trial\_command = 'python3 trial.py'

experiment.config.trial\_code\_directory = Path(\_\_file\_\_).parent

experiment.config.tuner.name = 'Evolution'

experiment.config.tuner.class\_args\['optimize\_mode'\] = 'maximize'

27

![](index-41_1.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

\# Starting NNI

http\_port = 8080

experiment.start(http\_port)

\# Event Loop

while True:

if experiment.get\_status() == 'DONE':

search\_data = experiment.export\_data()

search\_metrics = experiment.get\_job\_metrics()

input("Experiment is finished. Press any key to exit...")

break

Listin[g 1-7 con](#index_split_000.html#p40)tains an event loop that allows you to track the progress of your experiment automatically. Therefore, you can programmatically design experiments and get the best solutions for a problem.

**Troubleshooting**

If you experience any problems or errors launching and using NNI, you can follow this mini-guide to determine the issue.

**NNI is not starting**. In this case, you’ll see the error output message after running nnictl start command, and this error message can help you fix the problem.

**NNI is starting, but you see an ERROR badge** in the overview web panel, as shown in Figure [1-21](#index_split_000.html#p41).

***Figure 1-21.** NNI. Error badge*

28

![](index-42_1.png)

![](index-42_2.png)

Chapter 1 IntroduCtIon to neural network IntellIgenCe

In this case, please check error log file in ~/nni-experiments/<experiment\_id>/log/

nnictl\_stderr.log.

**NNI is starting. Experiment is RUNNING, but Trials have FAILED status**, as shown in Figure [1-22](#index_split_000.html#p42).

***Figure 1-22.** NNI. Failed Trials*

In this case, check Trial logs in Trial jobs panel, as shown in Figure [1-23.](#index_split_000.html#p42)

***Figure 1-23.** NNI. Trial logs*

This mini-guide may make it easier to find and fix the NNI problem.

**TensorFlow and PyTorch**

This book will apply AutoDL techniques to models implemented with **TensorFlow**

or **PyTorch**. This book assumes that the reader has experience with one of these frameworks. Each chapter will provide examples of applying NNI to a model

implemented in TensorFlow or PyTorch. Examples implemented on PyTorch or

29

Chapter 1 IntroduCtIon to neural network IntellIgenCe

TensorFlow will not duplicate each other but will be close to each other. Therefore, if you are only a PyTorch user, you will not lose anything if you do not dive into the examples with TensorFlow models.

This book will use the following framework versions:

• **TensorFlow**:

2.7.0

• **PyTorch**:

1.9.0

• **PyTorch Lightning**: 1.4.2

• **Scikit-learn**:

0.24.1

In any case, I recommend you to go through all examples because their concepts can be easily ported to your favorite deep learning framework.

**Summary**

In this chapter, we have explored the NNI basic features. NNI is a very powerful toolkit for solving various AutoML tasks. And at the beginning of this chapter, we separately investigated the demand to apply AutoML techniques in practice. In the next chapter, we will begin exploring the application of the classic Hyperparameter Optimization (**HPO**) approach. We will study how HPO techniques can optimize existing architectures and create a new model design.

30

**CHAPTER 2**

**Hyperparameter**

**Optimization**

Almost every deep learning model has a large number of hyperparameters. Choosing the proper hyperparameters is one of the most common problems in AutoML. A small change in one of the model’s hyperparameters can significantly change its performance.

Hyperparameter Optimization (HPO) is the first and most effective step in deep learning model tuning. Due to its ubiquity, Hyperparameter Optimization is sometimes regarded as synonymous with AutoML.

NNI provides a broad and flexible set of HPO tools. This chapter will examine various neural network designs and how NNI can be applied to optimize their hyperparameters for particular problems.

**What Is Hyperparameter?**

Let’s start the chapter by defining what a model *hyperparameter* is. A deep learning model has three types of parameters:

• **Weights and biases (or model parameters)**: Parameters of linear

(or tensor) functions in the neural network’s architecture, which are

tuned during its training.

• **Hyperparameters**: Initial global variables that are set manually and

affect the behavior of the functions, the training algorithm, and the

neural network’s architecture.

31

© Ivan Gridin 2022

I. Gridin, *Automated Deep Learning Using Neural Network Intelligence*,

[https://doi.org/10.1007/978-1-4842-8149-9\_2](https://doi.org/10.1007/978-1-4842-8149-9_2#DOI)

Chapter 2 hyperparameter OptimizatiOn

• **Task parameters**: The parameters that the task sets for you. These

parameters lie in the problem requirements, which need to be

satisfied and cannot be changed. For example, suppose we solve the

binary classification problem determining “cat or dog?” by analyzing

their pictures. In that case, we have a task parameter: **2**, which

indicates the number of output classes. Or, for example, we have the

air temperature prediction problem for the next three days. Then

parameter 3 is a task parameter, and it lies in the task requirements

and cannot be changed in any way.

Let’s look at an example of a Fully Connected Neural Network (or Dense Network)

with three linear (or dense) layers with activation functions and five-valued input vector and scalar output, which can be represented as follows in the TensorFlow framework: We import necessary packages:

***Listing 2-1.*** Fully Connected Neural Network. ch2/hpo\_definition/fcnn\_

model.py

import tensorflow as tf

from tensorflow.keras.layers import Dense

Next, we set task parameters which are task requirements. Our Fully Connected

Neural Network has to receive five-valued input vector and output a scalar value:

\# Task Parameters

inp\_dim = 5

out\_dim = 1

Since we have three linear (or dense) layers, we can specify the output\_dimension value for two of them. The third layer has an output\_dimension value of 1 because this is a task requirement. These values are hyperparameters:

\# Hyperparameters

l1\_dim = 8

l2\_dim = 4

32

Chapter 2 hyperparameter OptimizatiOn

We initialize the FCNN model:

\# Model

model = tf.keras.Sequential(

\[

Dense(l1\_dim, name = 'l1',

activation = 'sigmoid', input\_dim = inp\_dim),

Dense(l2\_dim, name = 'l2',

activation = 'relu'),

Dense(out\_dim, name = 'l3'),

\]

)

model.build()

And here we have FCNN model parameters:

\# Weights and Biases

print(model.summary())

which are presented in Ta[ble 2-1.](#index_split_000.html#p46)

***Table 2-1.** FCNN model weights and biases*

**Layer**

**Output Shape**

**Param #**

**Explained**

l1

(None, 8)

48

5×8 weight matrix + 8 bias vector = 48

l2

(None, 4)

36

8×4 weight matrix + 4 bias vector = 36

l3

(None, 1)

5

4×1 weight matrix + 1 bias vector = 5

Total params: 89

The model shown in Listin[g 2-1 h](#index_split_000.html#p45)as 2 hyperparameters and 89 model parameters.

Hyperparameters usually directly affect the number of model parameters. Indeed,

in Listing [2-1](#index_split_000.html#p45), the l1\_dim and l2\_dim hyperparameters set the dimensions of weight matrices and bias vectors. Figure [2-1](#index_split_000.html#p47) illustrates the hyperparameter impact on the FCNN

model architecture and its parameters.

33

![](index-47_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-1.** Hyperparameter impact*

We can distinguish four types of hyperparameters:

• ***Layer*** hyperparameter

• ***Training*** hyperparameter

• ***Feature*** hyperparameter

• ***Design*** hyperparameter

Let’s examine each of these hyperparameter types.

34

Chapter 2 hyperparameter OptimizatiOn

**Layer Hyperparameter**

Almost all layers of a deep learning model imply the presence of initial parameters. For example:

• **Dropout layer**: Assumes *p* (0 < *p* < 1) parameter, which defines dropout probability

• **MaxPool 2D layer**: Assumes pool\_size parameter, which defines the

pooling dimension

• **Convolutional 2D layer**: Assumes kernel\_size parameter

We can refer to these hyperparameters as *layer hyperparameters*.

**Training Hyperparameter**

The training process is an integral part of the model architecture. Each model generates a multidimensional loss function surface. The model training process tries to find the best local minima on the loss function surface. The training process parameters can drastically affect trained model performance.

The most common example is *learning rate* tuning. Most training algorithms use gradient descent as the main idea behind model training. The gradient descent concept means that a transition vector is calculated for each point on the loss function surface. But the length of this vector is determined by the *learning rate* parameter. Too high *learning rate* parameter can lead to a gradient descent explosion and a complete inability to find an acceptable local minima on the loss function surface. At the same time, too low *learning rate* stops the training process at a too high point on the surface and does not allow model parameters to reach a lower point. Figur[e 2-2 demons](#index_split_000.html#p49)trates the learning rate problem.

35

![](index-49_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-2.** Learning rate problem*

The most common training hyperparameters are

• *Training epochs number*

• *Learning rate*

• *Batch size*

Layer Hyperparameter and Training Hyperparameter Optimization is the most

common way to tune a model due to the ease of this approach implementation.

**Feature Hyperparameter**

Feature hyperparameter affects dataset preprocessing methods. The data structure in the input dataset can significantly improve the model’s performance, especially in natural language processing (NLP) problems. But transformations of the input dataset do not always improve the model’s performance, so you often have to “play” with various feature preprocessing techniques to reach the best results.

Let’s examine a dataset that contains movie reviews data. This dataset includes the following features:

• **Feature** ***A***: Movie budget ( *example: 100 000 000$*)

• **Feature** ***B***: Review date ( *example: 2021-05-03*)

• **Feature** ***C***: Review text ( *example: I love good movies, but* *unfortunately, this is not one of them*.)

36

![](index-50_1.png)

Chapter 2 hyperparameter OptimizatiOn

And we are solving the classical binary classification problem, that is, we have to determine whether the review is negative or positive. Then we can apply the following preprocessing, which is shown in Figure [2-3](#index_split_000.html#p50).

***Figure 2-3.** Dataset preprocessing driven by feature hyperparameters*

The dataset preprocessing shown in Figur[e 2-3 h](#index_split_000.html#p50)as the following feature hyperparameters: *use Normalization*, *use Weekend labeling*, and *use Stop words removal*.

Let’s describe their meanings:

37

Chapter 2 hyperparameter OptimizatiOn

• ***use Normalization:***

Normalization is a common technique for converting numeric

data by converting all values to the range from 0 to 1. *use*

*Normalization* hyperparameter manages the application of

normalization to feature A (budget):

• **0**: Normalization is not applied to feature A.

• **1**: Normalization is applied to feature A and produces À feature.

• ***use Weekend labeling:***

The date does not carry any information for the neural network.

But an extra datetime labeling might help. For example, reviews

left on holidays can be positive more often because people are

in a good mood. Then we can use the weekend labeling method,

which will label each date if it is a holiday or a weekend. Date

series can then be converted from *2021-11-05*, *2021-11-06*,

*2021-11-07*, … to 0, 1, 1, ….

• **0**: Weekend labeling is not applied, and feature B is removed from

the dataset.

• **1**: Weekend labeling is applied, and feature B is converted to

feature B’.

• ***use Stop words removal:***

Removing stop words from text is a common practice that cleans

the text from noise. Stop words removal often helps speed up

training and improve the quality of an NLP model.

• **0**: Stop words removal is not applied to feature C.

• **1**: Stop words removal is applied to feature C and produces

feature C\`.

For example, this combination of feature hyperparameters { *use Normalization*: 0, *use* *Weekend labeling*: 1, *use Stop words removal*: 1} will transform original dataset \[A, B, C\]

to \[A, B’, C’\].

38

![](index-52_1.png)

Chapter 2 hyperparameter OptimizatiOn

**Design Hyperparameter**

Design hyperparameter has a direct impact on the choice of neural network architecture.

Their values control the choice of neural network layers and connections between them.

Figur[e 2-4 sho](#index_split_000.html#p52)ws design hyperparameters.

***Figure 2-4.** Design hyperparameters*

The design hyperparameter search shown in Figur[e 2-4 h](#index_split_000.html#p52)as the following design hyperparameters: *use Dropout*, *use MaxPool*, and *Activation function*. And they affect the model design the following way:

• ***use Dropout*****:**

• **0**: *Dropout layer* is skipped.

• **1**: *Dropout layer* is connected.

39

Chapter 2 hyperparameter OptimizatiOn

• ***use MaxPool*****:**

• **0**: *MaxPool layer* is skipped.

• **1**: *Max Poll layer* is connected.

• ***Activation function*****:**

• **1**: *Sigmoid activation* function is connected.

• **2**: *Hyperbolic tangent activation* function is connected.

• **3**: *Rectified linear activation* function is connected.

For example, this combination of design hyperparameters { *use Dropout*: 1, *use* *MaxPool*: 0, *Activation function*: 3} will generate the following sequence of layers in the neural network architecture:

• Linear layer

• Dropout layer

• ReLU activation

• Linear layer

Design Hyperparameter Optimization is used less often because it is more

challenging to implement than Layer Hyperparameter or Training Hyperparameter

Optimization. But design hyperparameter tuning can produce great results. It chooses the best combination of layers and connections between them for a particular problem.

Design Hyperparameter Optimization can be considered as an intermediate approach between Hyperparameter Optimization and Neural Architecture Search.

**Search Space**

Say we have determined the model’s hyperparameters, which will need to be optimized.

Next, we must define a search space for each of the hyperparameters. Determining the search space requires some experience and intuition. You must understand that the larger the search space, the longer the experiment. And it is more difficult to find a suitable solution. Therefore, it is pointless to specify a huge number of values in the search space. For example, if l1 is a hyperparameter that specifies the dimension of a linear layer (tensorflow.keras.layers.Dense(l1) or torch.nn.Linear(out\_features

\= l1)), then you don’t need to set the search space for the hyperparameter to

40

Chapter 2 hyperparameter OptimizatiOn

\[1, 2, 3,..., 999, 1000\]. For the hyperparameter l1, values expressing the power of two (2n) are more suitable: \[4, 8, 16, ..., 256\], because the representation size of linear layers is relevant only proportionally, not additively (if l1 = 256 performed poorly, thus, it is highly likely that l1 = 256 + 8 will show the same result). A reasonable choice of hyperparameters can significantly reduce the time of the experiment without losing its quality. Before specifying a search space, you can perform manual exploration to determine which hyperparameter values have the most impact on model performance.

The search space for the HPO problem is defined by defining a set of possible

values for each of the hyperparameters. NNI allows the following sampling strategies to define hyperparameter search space: choice, randint, uniform, quniform, loguniform, qloguniform, normal, qnormal, lognormal, and qlognormal.

**choice**

{"\_type": "choice", "\_value": options}

Choice sampling strategy allows you to manually specify a list of values that a hyperparameter can take. It can be a list of numbers and strings. For example:

"hp": {"\_type": "choice", "\_value": \[128, 512, 1024\]}

Choice sampling also supports nested search spaces. Nested choice is especially

useful when dealing with design hyperparameters. Here is the example of nested choice sampling:

**"** layer1**"** :{

"\_type": "choice",

"\_value": \[{"\_name": "Empty"},

{

"\_name": "Conv", "kernel\_size":

{"\_type": "choice", "\_value": \[1, 2, 3, 5\]}

},

{

"\_name": "Max\_pool", "pooling\_size":

{"\_type": "choice", "\_value": \[2, 3, 5\]}

},

41

Chapter 2 hyperparameter OptimizatiOn

{

"\_name": "Avg\_pool", "pooling\_size":

{"\_type": "choice", "\_value": \[2, 3, 5\]}

}

\]

}

**randomint**

{"\_type": "randint", "\_value": \[lower, upper\]}

Chooses random integer from lower (inclusive) to upper (exclusive).

**uniform**

{"\_type": "uniform", "\_value": \[low, high\]}

Chooses random value according to uniform distribution on \[low, high\].

**quniform**

{"\_type": "quniform", "\_value": \[low, high, q\]}

Acts like uniform sampling but with q discretization that can be expressed as

clip(round(uniform(low, high) / q) \* q, low, high). For example, for \_value

specified as \[1, 11, 2.5\], possible values are \[1, 2.5, 5, 7.5, 10, 11\].

**loguniform**

{"\_type": "loguniform", "\_value": \[low, high\]}

Chooses random value according to loguniform distribution on \[low, high\] that can be expressed as np.exp(uniform(np.log(low), np.log(high))).

42

Chapter 2 hyperparameter OptimizatiOn

**qloguniform**

{"\_type": "qloguniform", "\_value": \[low, high, q\]}

Acts like loguniform sampling but with q discretization that can be expressed as clip(round(loguniform(low, high) / q) \* q, low, high).

**normal**

{"\_type": "normal", "\_value": \[mu, sigma\]}

Chooses random value according to normal distribution with μ = mu and σ = sigma.

**qnormal**

{"\_type": "qnormal", "\_value": \[mu, sigma, q\]}

Acts like normal sampling but with q discretization that can be expressed as

round(normal(mu, sigma) / q) \* q.

**lognormal**

{"\_type": "lognormal", "\_value": \[mu, sigma\]}

Chooses random value according to lognormal distribution with μ = mu and σ = sigma that can be expressed as np.exp(normal(mu, sigma)).

**qlognormal**

{"\_type": "qlognormal", "\_value": \[mu, sigma, q\]}

Acts like lognormal sampling but with q discretization that can be expressed as

round(exp(normal(mu, sigma)) / q) \* q.

The implementation of sampling strategies is in nni.parameter expressions. You

can explore search space sampling strategies manually, as shown in Listin[g 2-2.](#index_split_000.html#p57)

43

![](index-57_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Listing 2-2.*** quniform sampling strategy. ch2/search\_space/quniform.py import nni

from numpy.random.mtrand import RandomState

import matplotlib.pyplot as plt

We generate 20 samples using quniform strategy:

space = \[

nni.quniform(0, 100, 5, RandomState(seed))

for seed in range(20)

\]

Visualize generated samples:

plt.figure(figsize = (5, 1))

plt.title('quniform')

plt.plot(space, len(space) \* \[0\], "x")

plt.yticks(\[\])

plt.show()

And after, you can observe generated samples using quniform method in Figur[e 2-5.](#index_split_000.html#p57)

***Figure 2-5.** quniform samples*

Let’s examine an example of a JSON search space definition.

***Listing 2-3.*** Search space. ch2/search\_space/search\_space.json

{

"dropout\_rate":

{ "\_type": "uniform", "\_value": \[0.1, 0.5\]},

"conv\_size":

{"\_type": "choice", "\_value": \[2, 3, 5, 7\]},

44

Chapter 2 hyperparameter OptimizatiOn

"layer1\_hidden\_size":

{"\_type": "choice", "\_value": \[128, 512, 1024\]},

"layer2\_hidden\_size":

{"\_type": "choice", "\_value": \[16, 32, 64\]},

"activation\_function":

{"\_type": "choice", "\_value": \["tanh", "sigmoid", "relu"\]},

"training\_batch\_size":

{"\_type": "choice", "\_value": \[100, 250, 500\]},

"training\_learning\_rate":

{"\_type": "uniform", "\_value": \[0.0001, 0.1\]}

}

Listin[g 2-3 demons](#index_split_000.html#p57)trates a typical search space for deep learning model:

• **dropout\_rate**: Layer hyperparameter that defines the *p* parameter in dropout layer. dropout\_rate can take any value from 0.1 to 0.5.

• **conv\_size**: Layer hyperparameter that defines the kernel size of

convolutional layer. conv\_size can take any value from the list: 2,

3, 5, 7.

• **layer1\_hidden\_size**: Layer hyperparameter that defines the output

dimension of the first linear layer. layer1\_hidden\_size can take any

value from the list: 128, 512, 1024.

• **layer2\_hidden\_size**: Layer hyperparameter that defines the output

dimension of the second linear layer. layer2\_hidden\_size can take

any value from the list: 16, 32, 64.

• **activation\_function**: Design hyperparameter that defines output

activation function. activation\_function can take any value from

the list: tanh, sigmoid, relu.

• **training\_batch\_size**: Training hyperparameter that defines batch

size that will be used during training. training\_batch\_size can take

any value from the list: 100, 250, 500.

• **training\_learning\_rate**: Training hyperparameter that defines

learning rate. training\_learning\_rate can take any value from

0.0001 to 0.1.

45

Chapter 2 hyperparameter OptimizatiOn

**Tuners**

After defining the search space, we need to define a tuner that will explore the search space and select trial hyperparameter combinations based on the existing results.

The tuner is set as follows in the configuration file:

tuner:

name: <Tuner\_Name>

classArgs:

optimize\_mode: minimize

arg1: val1

arg2: val2

Each tuner has its own set of parameters. The only common parameter for all

tuners is optimize\_mode, which marks the direction of optimization of the metric that characterizes the model’s performance: minimize, maximize.

Table [2-2](#index_split_000.html#p59) provides the list of tuners available in NNI v2.7.

***Table 2-2.** Search Tuners*

**Configuration Id**

**Name**

SMAC

Sequential model-Based Optimization

TPE

tree-structured parzen estimator

Random

random Search

Anneal

annealing Search algorithm

Evolution

Genetic algorithm Search

BatchTuner

Batch tuner

GridSearch

Grid Search

NetworkMorphism

network morphism

MetisTuner

metis tuner

GPTuner

Gaussian process (Gp) tuner

PBTTuner

population-Based training tuner

46

![](index-60_1.png)

Chapter 2 hyperparameter OptimizatiOn

We will study tuning algorithms in detail in Chapt[er 3](https://doi.org/10.1007/978-1-4842-8149-9_3). In this chapter, we will consider only **Random Search Tuner** and **Grid Search Tuner**.

**Random Search Tuner**

The Random Search Tuner is the most straightforward approach to choosing

a combination of hyperparameters. As the name implies, the combination of

hyperparameters is chosen absolutely randomly. Despite the simplicity of this approach, it can sometimes give very good results.

Random Search Tuner is set as

tuner:

name: Random

Figur[e 2-6 illus](#index_split_000.html#p60)trates the Random Search Tuner in action.

***Figure 2-6.** Random Search Tuner*

In some cases, Random Search Tuner is well suited for exploring the search

space when you need to extract information about hyperparameters’ impact on

model performance. After a random search space exploration, you can redefine

hyperparameter search space and select another tuner.

47

![](index-61_1.png)

Chapter 2 hyperparameter OptimizatiOn

**Grid Search Tuner**

Grid Search Tuner performs an exhaustive search, that is, Grid Search Tuner will search all the possible combinations from the search space. Grid Search Tuner is well suited for small search spaces.

Grid Search Tuner is set as

tuner:

name: GridSearch

Figur[e 2-7 illus](#index_split_000.html#p61)trates the Grid Search Tuner in action.

***Figure 2-7.** Grid Search Tuner*

Grid Search Tuner accepts only search space variables that are generated with

choice, quniform, and randint functions.

**Organizing Experiment**

And so, we are all set to begin our first explorations. Let’s look at the file organization pattern we’ll be using in this book. I also recommend that you follow the same approach.

These simple rules will help you avoid unnecessary errors when running an

experiment:

• Use a separate directory for each experiment.

• Specify the current directory as trial code directory in the experiment

configuration.

48

Chapter 2 hyperparameter OptimizatiOn

• Keep the model class and training/testing methods in a separate file.

• Add root code folder to the system path in trial file.

• Do not mix model and trial files.

Let’s look at a dummy experiment that follows these rules ch2/experiment\_pattern.

Listin[g 2-4 pr](#index_split_000.html#p62)ovides the experiment configuration file.

The configuration file marks the current directory as the working directory:

trialCodeDirectory: .

***Listing 2-4.*** Experiment configuration. ch2/experiment\_pattern/config.yml trialConcurrency: 1

searchSpaceFile: search\_space.json

trialCodeDirectory: .

trialCommand: python3 trial.py

tuner:

name: GridSearch

trainingService:

platform: local

Model class and training/testing methods are in a separate file shown in Listin[g 2-5.](#index_split_000.html#p62)

***Listing 2-5.*** DummyModel class. ch2/experiment\_pattern/model.py

from random import random

class DummyModel:

def \_\_init\_\_(self, x, y) -> None:

super().\_\_init\_\_()

self.x = x

self.y = y

def train(self):

\# Training here

...

def test(self):

\# Test results

return round(self.x + self.y + random() / 10, 2)

49

Chapter 2 hyperparameter OptimizatiOn

***Table 2-3.** NNI API*

**Method**

**Description**

nni.get\_next\_parameter()

required method that receives trial parameters

from nni tuner as Dict object

nni.report\_intermediate\_result(m)

Optional method that sends intermediate results to

nni tuner

nni.report\_final\_result(m)

required method that sends final metrics that

represents model’s performance

The trial script receives parameters from the NNI tuner, initializes the model, trains it, and tests its performance. The trial script interacts with NNI using the following API methods shown in Table [2-3.](#index_split_000.html#p63)

Let’s look at the trial script pattern in Listin[g 2-6.](#index_split_000.html#p63)

We import necessary modules:

***Listing 2-6.*** Trial script pattern. ch2/experiment\_pattern/trial.py import os

import sys

import nni

And here, we add the root directory of the code to the system path. This is done because NNI has no idea about the structure of our code and the location of modules.

\# For NNI use relative import for user-defined modules

SCRIPT\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_)) + '/../..'

sys.path.append(SCRIPT\_DIR)

Now, we can import the classes we need from our code structure:

from ch2.experiment\_pattern.model import DummyModel

50

Chapter 2 hyperparameter OptimizatiOn

Trial initiates the model, trains it, measures its performance, and returns the result to NNI Tuner:

def trial(hparams):

"""

Trial Script:

\- Initiate Model

\- Train

\- Test

\- Report

"""

model = DummyModel(\*\*hparams)

model.train()

accuracy = model.test()

\# send final accuracy to NNI

nni.report\_final\_result(accuracy)

And here is the entry point to the trial script:

if \_\_name\_\_ == '\_\_main\_\_':

\# Manual HyperParameters

hparams = {

'x': 1,

'y': 1,

}

\# NNI HyperParameters

\# Run safely without NNI Experiment Context

nni\_hparams = nni.get\_next\_parameter()

hparams.update(nni\_hparams)

trial(hparams)

You can run trial script ch2/experiment\_pattern/trial.py in stand-alone mode.

It means you can run this script without getting any errors. The nni.get\_next\_

parameter() method will return an empty dict that you can merge with your trial

parameters. This is convenient if you want to test trial execution.

51

![](index-65_1.png)

Chapter 2 hyperparameter OptimizatiOn

Experiment file structure pattern can be depicted as it is shown in Figure [2-8](#index_split_000.html#p65).

***Figure 2-8.** Experiment file structure*

Fine! We’ve defined different hyperparameter types, examined how to define search spaces, studied simple tuners, and represented a pattern for creating experiments. We are now ready to move on to real research. The following sections will examine how HPO methods optimize the model for the specific problem and help develop a new

model design.

**Optimizing LeNet for MNIST Problem**

Libraries: TensorFlow (Keras API), PyTorch

MNIST Classifier problem is a common problem to test various machine learning

approaches. Convolutional neural networks have made a breakthrough in image

recognition, so we also use the MNIST dataset for diving into the HPO area. The MNIST

database contains images of handwritten digits. It is split into two sets: a training set of 60,000 samples and a test set of 10,000 examples. Figur[e 2-9 dis](#index_split_000.html#p66)plays several samples from the MNIST dataset.

52

![](index-66_1.jpg)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-9.** MNIST database*

MNIST dataset is a set of 28×28 grayscale images. Therefore, each dataset object is a (28, 28, 1) tensor. Let’s examine several samples of this dataset.

***Listing 2-7.*** MNIST dataset samples. ch2/lenet\_hpo/mnist\_dataset.py import tensorflow\_datasets as tfds

ds, info = tfds.load('mnist', split = 'train', with\_info = True)

fig = tfds.show\_examples(ds, info)

fig.show()

Listin[g 2-7 dis](#index_split_000.html#p66)plays the image in Figure [2-10.](#index_split_000.html#p67)

53

![](index-67_1.png)

![](index-67_2.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-10.** MNIST samples*

This may seem like a very simple task, but it is not. Recall how often you could not understand the number written down by another person’s hand. Handwritten

digit recognition was one of the first fundamental problems of pattern recognition.

LeNet-5 is one of the earliest neural networks used for recognizing handwritten and machine-printed characters. The main reason behind the popularity of this model was its straightforward architecture. It is a multilayer convolution neural network for image classification. Abstract LeNet model design is depicted in Figur[e 2-11](#index_split_000.html#p67).

***Figure 2-11.** LeNet architecture*

54

Chapter 2 hyperparameter OptimizatiOn

Our goal is to optimize the LeNet model to the handwritten digit recognition

problem. The easiest thing is to start Layer Hyperparameter Optimization. Let’s just count the number of layer hyperparameters in the LeNet model:

• **Conv2D layer**: Five basic hyperparameters (out\_channels,

kernel\_size, stride, padding, dilation)

• **MaxPool2D layer**: Two basic hyperparameters

(kernel\_size, stride)

• **Linear layer:** Two basic hyperparameters (out\_features, use\_bias)

LeNet contains two Conv2D layers, two MaxPool2D layers, and two linear layers.

Thus, we have 2×5 + 2×2 + 2×2 = 14 layer hyperparameters in LeNet model. Let’s assume that for each hyperparameter, we will have a set of possible values that will consist of only two elements, although, of course, many hyperparameters require more values for the flexibility of the experiment. But even this binary search space contains 214 = 16 384

elements. And these are just the most primitive layer hyperparameters for one of the simplest deep learning models. As the complexity of the model increases, the number of possible hyperparameters in it grows exponentially. Even the most advanced tuner can take a very long time to explore this search space. Therefore, we need some experience and intuition, which will allow us to select the critical hyperparameter range for each model without increasing the search space too much.

Let’s consider only the following layer hyperparameters:

• **Conv2D layer 1**: filter\_size\_1, kernel\_size\_1

• **Conv2D layer 2**: filter\_size\_2, kernel\_size\_2

• **Linear layer**: out\_features

In order to reduce the size of the search space, we set

• filter\_size\_2 = 2 \* filter\_size\_1

• kernel\_size\_1 = kernel\_size\_2

Then, we will focus on only three hyperparameters for LeNet model:

• filter\_size

• kernel\_size

• out\_features

55

Chapter 2 hyperparameter OptimizatiOn

Usually, the best values for the filter\_size of the convolutional layer are presented as 2n. Therefore, we will choose the following ones for the search space: 8, 16, 32. The kernel\_size values are usually chosen in a set of 2n + 1. And the larger the image is, the larger kernel\_size value should be chosen. The samples of the MNIST dataset are 28×28 images. These are pretty small images, so we shouldn’t choose large kernel\_size values: 2, 3, 5. The best values for l1\_size are powers of two, as for filter\_size. The linear layer is applied to the tensor after the flatten layer, which means that we have to consider the dimension of the tensor that the previous layers will produce. In the case of the MNIST problem, we will focus on the following l1\_size values: 32, 64, 128. For MaxPool2D layer we will set the lowest possible value of pool\_size, which is 2, and set sigmoid as the activation function. Yes! That’s the function that has been used for quite a long time as an activation function for most pattern recognition problems. We will return to the problem of choosing an activation function in the next section.

We will use classic batch neural network training with Adam optimizer. So let’s now look at training hyperparameters. I suggest starting the study by selecting the simplest hyperparameters: batch\_size and learning rate. The best parameters for batch\_

size are expressed as 2n and learning\_rate as 10-n. For this case, we will choose the following: 256, 512, 1024 for batch\_size and 0.01, 0.001, 0.0001 for learning\_rate.

Now let’s convert the hyperparameter constraints we made earlier into NNI search space. Listin[g 2-8](#index_split_000.html#p69) defines the search space for LeNet hyperparameter optimization search space.

***Listing 2-8.*** LeNet HPO search space. ch2/lenet\_hpo/search\_space.json

{

"filter\_size": {

"\_type": "choice", "\_value": \[8, 16, 32\]},

"kernel\_size": {

"\_type": "choice", "\_value": \[2, 3, 5\]},

"l1\_size": {

"\_type": "choice", "\_value": \[32, 64, 128\]},

"batch\_size": {

"\_type": "choice", "\_value": \[256, 512, 1024\]},

"learning\_rate": {

"\_type": "choice", "\_value": \[0.01, 0.001, 0.0001\]}

}

56

Chapter 2 hyperparameter OptimizatiOn

Fine! In the next step, we will create TensorFlow and PyTorch implementations of the LeNet model considering the HPO problem.

**TensorFlow LeNet Implementation**

In this section, we will study the LeNet model’s implementation using TensorFlow (Keras API). Listing [2-9](#index_split_000.html#p70) demonstrates the implementation of the TensorFlow LeNet model for the hyperparameter optimization.

We import necessary modules:

***Listing 2-9.*** LeNet. TensorFlow implementation. ch2/lenet\_hpo/tf\_lenet\_

model.py

from tensorflow.keras import Model

from tensorflow.keras.layers import Conv2D, Dense, Flatten, MaxPool2D

from tensorflow.keras.optimizers import Adam

from ch2.utils.datasets import mnist\_dataset

from ch2.utils.tf\_utils import TfNniIntermediateResult

Next, we define the LeNet model with three layer hyperparameters:

class TfLeNetModel(Model):

def \_\_init\_\_(self, filter\_size, kernel\_size, l1\_size):

super().\_\_init\_\_()

First convolutional stack:

self.conv1 = Conv2D(

filters = filter\_size,

kernel\_size = kernel\_size,

activation = 'sigmoid'

)

self.pool1 = MaxPool2D(pool\_size = 2)

Second convolutional stack:

self.conv2 = Conv2D(

filters = filter\_size \* 2,

kernel\_size = kernel\_size,

57

Chapter 2 hyperparameter OptimizatiOn

activation = 'sigmoid'

)

self.pool2 = MaxPool2D(pool\_size = 2)

Dense stack:

self.flatten = Flatten()

self.fc1 = Dense(

units = l1\_size,

activation = 'sigmoid'

)

self.fc2 = Dense(

units = 10,

activation = 'softmax'

)

LeNet is a straightforward model which passes calculation results from one layer to another:

def call(self, x, \*\*kwargs):

x = self.conv1(x)

x = self.pool1(x)

x = self.conv2(x)

x = self.pool2(x)

x = self.flatten(x)

x = self.fc1(x)

return self.fc2(x)

The training method uses two training hyperparameters: batch\_size and learning

rate. We use Adam optimizer with categorical cross-entropy loss function:

def train(self, learning\_rate, batch\_size):

self.compile(

optimizer = Adam(learning\_rate = learning\_rate),

loss = 'sparse\_categorical\_crossentropy',

metrics = \['accuracy'\]

)

(x\_train, y\_train), \_ = mnist\_dataset()

58

Chapter 2 hyperparameter OptimizatiOn

Next, we initialize a callback that sends intermediate results to NNI:

intermediate\_cb = TfNniIntermediateResult('accuracy')

Performing classic batch training with ten epochs:

self.fit(

x\_train,

y\_train,

batch\_size = batch\_size,

epochs = 10,

verbose = 0,

callbacks = \[intermediate\_cb\]

)

And the last method we need to define is model testing. We load the test MNIST

dataset and perform the classification by measuring its accuracy:

def test(self):

"""Testing Trained Model Performance"""

(\_, \_), (x\_test, y\_test) = mnist\_dataset()

loss, accuracy = self.evaluate(x\_test, y\_test, verbose = 0)

return accuracy

Well, since the implementation of TensorFlow LeNet model is ready, we can

implement the NNI trial script using Listin[g 2-10](#index_split_000.html#p72).

We import necessary modules and pass code root directory to system path:

***Listing 2-10.*** NNI trial script with TensorFlow LeNet implementation. ch2/lenet\_

hpo/tf\_trial.py

import os

import sys

import nni

\# For NNI use relative import for user-defined modules

SCRIPT\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_)) + '/../..'

sys.path.append(SCRIPT\_DIR)

from ch2.lenet\_hpo.tf\_lenet\_model import TfLeNetModel

59

Chapter 2 hyperparameter OptimizatiOn

The trial method initializes the model, trains it, tests it, and returns the NNI metric: def trial(hparams):

model = TfLeNetModel(

filter\_size = hparams\['filter\_size'\],

kernel\_size = hparams\['kernel\_size'\],

l1\_size = hparams\['l1\_size'\]

)

model.train(

batch\_size = hparams\['batch\_size'\],

learning\_rate = hparams\['learning\_rate'\]

)

accuracy = model.test()

\# send final accuracy to NNI

nni.report\_final\_result(accuracy)

And finally, we define the main entry point for the trial:

if \_\_name\_\_ == '\_\_main\_\_':

\# Manual HyperParameters

hparams = {

'filter\_size': 32,

'kernel\_size': 3,

'l1\_size': 64,

'batch\_size': 512,

'learning\_rate': 1e-3,

}

\# NNI HyperParameters

\# Run safely without NNI Experiment Context

nni\_hparams = nni.get\_next\_parameter()

hparams.update(nni\_hparams)

trial(hparams)

Remember that a trial script can be executed in stand-alone mode, so you can run a ch2/lenet\_hpo/tf\_trial.py to test its execution with custom parameters.

60

Chapter 2 hyperparameter OptimizatiOn

**PyTorch LeNet Implementation**

In this section, we will study the LeNet model’s implementation using

PyTorch. Listing [2-11](#index_split_000.html#p74) demonstrates the implementation of the PyTorch LeNet model for the hyperparameter optimization.

We import necessary modules:

***Listing 2-11.*** LeNet. PyTorch implementation. ch2/lenet\_hpo/pt\_lenet\_

model.py

import numpy as np

import nni

import torch

import torch.nn as nn

import torch.nn.functional as F

import torch.optim as optim

from sklearn.metrics import accuracy\_score

from ch2.utils.datasets import mnist\_dataset

Next, we define the LeNet model with three layer hyperparameters:

class PtLeNetModel(nn.Module):

def \_\_init\_\_(self, filter\_size, kernel\_size, l1\_size):

super(PtLeNetModel, self).\_\_init\_\_()

This implementation will use lazy layer initialization, so we explicitly save the l1\_

size hyperparameter:

\# Saving l1\_size HyperParameter

self.l1\_size = l1\_size

After that, we initialize convolutional layers:

self.conv1 = nn.Conv2d(

in\_channels = 1,

out\_channels = filter\_size,

kernel\_size = kernel\_size

)

61

Chapter 2 hyperparameter OptimizatiOn

self.conv2 = nn.Conv2d(

in\_channels = filter\_size,

out\_channels = filter\_size \* 2,

kernel\_size = kernel\_size

)

We don’t initialize the first linear layer, but we use lazy initialization. To initialize a linear layer, we must specify an in\_features value. But this is not so simple. We need to know the dimension of the tensor, which the previous layers will produce. To do this, sometimes, you have to do complex calculations. It is easier to calculate the dimension of this tensor at the first call and at this moment initialize the linear layer.

\# Lazy fc1 Layer Initialization

self.fc1\_\_in\_features = 0

self.\_fc1 = None

self.fc2 = nn.Linear(l1\_size, 10)

Lazy layer initialization:

@property

def fc1(self):

if self.\_fc1 is None:

self.\_fc1 = nn.Linear(

self.fc1\_\_in\_features,

self.l1\_size

)

return self.\_fc1

LeNet is a straightforward model which passes calculation results from one layer to another:

def forward(self, x):

x = torch.sigmoid(self.conv1(x))

x = F.max\_pool2d(x, 2, 2)

x = torch.sigmoid(self.conv2(x))

x = F.max\_pool2d(x, 2, 2)

62

Chapter 2 hyperparameter OptimizatiOn

\# Flatting all dimensions but batch-dimension

if not self.fc1\_\_in\_features:

self.fc1\_\_in\_features = np.prod(x.shape\[1:\])

x = x.view(-1, self.fc1\_\_in\_features)

\# FC1 initializes lazy

x = torch.sigmoid(self.fc1(x))

x = self.fc2(x)

return F.log\_softmax(x, dim = 1)

The training method uses two training hyperparameters: batch\_size and

learning rate:

def train\_model(self, learning\_rate, batch\_size):

We prepare training dataset:

(x, y), \_ = mnist\_dataset()

x = torch.from\_numpy(x).float()

y = torch.from\_numpy(y).long()

\# Permute dimensions for PyTorch Convolutions

x = torch.permute(x, (0, 3, 1, 2))

dataset\_size = x.shape\[0\]

Initialize Adam optimizer:

optimizer = optim.Adam(

self.parameters(),

lr = learning\_rate

)

Vanilla PyTorch does not have built-in batch training. Therefore, we manually split the dataset into batches and perform epoch loop and batch loop:

self.train()

for epoch in range(1, 10 + 1):

\# Random permutations for batch training

permutation = torch.randperm(dataset\_size)

for bi in range(1, dataset\_size, batch\_size):

63

Chapter 2 hyperparameter OptimizatiOn

\# Creating New Batch

indices = permutation\[bi:bi + batch\_size\]

batch\_x, batch\_y = x\[indices\], y\[indices\]

Model parameter optimization using cross-entropy loss function:

optimizer.zero\_grad()

output = self(batch\_x)

loss = F.cross\_entropy(output, batch\_y)

loss.backward()

optimizer.step()

At the end of each epoch, we calculate the model accuracy and return it to NNI as an intermediate result:

output = self(x)

predict = output.argmax(dim = 1, keepdim = True)

accuracy = round(accuracy\_score(predict, y), 4)

print(F'Epoch: {epoch}| Accuracy: {accuracy}')

\# report intermediate result

nni.report\_intermediate\_result(accuracy)

And the last method we need to define is model testing. We load the test MNIST

dataset and perform the classification by measuring its accuracy:

def test\_model(self):

self.eval()

\# Preparing Test Dataset

\_, (x, y) = mnist\_dataset()

x = torch.from\_numpy(x).float()

y = torch.from\_numpy(y).long()

x = torch.permute(x, (0, 3, 1, 2))

with torch.no\_grad():

output = self(x)

predict = output.argmax(dim = 1, keepdim = True)

accuracy = round(accuracy\_score(predict, y), 4)

return accuracy

64

Chapter 2 hyperparameter OptimizatiOn

Well, since the implementation of PyTorch LeNet model is ready, we can implement the NNI trial script using Listin[g 2-12](#index_split_000.html#p78).

We import necessary modules and pass code root directory to system path:

***Listing 2-12.*** NNI trial script with TensorFlow LeNet implementation. ch2/lenet\_

hpo/pt\_trial.py

import os

import sys

import nni

\# For NNI use relative import for user-defined modules

SCRIPT\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_)) + '/../..'

sys.path.append(SCRIPT\_DIR)

from ch2.lenet\_hpo.pt\_lenet\_model import PtLeNetModel

The trial method initializes the model, trains it, tests it, and returns the NNI metric: def trial(hparams):

model = PtLeNetModel(

filter\_size = hparams\['filter\_size'\],

kernel\_size = hparams\['kernel\_size'\],

l1\_size = hparams\['l1\_size'\]

)

model.train\_model(

batch\_size = hparams\['batch\_size'\],

learning\_rate = hparams\['learning\_rate'\]

)

accuracy = model.test\_model()

nni.report\_final\_result(accuracy)

And finally, we define the main entry point for the trial:

if \_\_name\_\_ == '\_\_main\_\_':

\# Manual HyperParameters

hparams = {

'filter\_size': 32,

'kernel\_size': 3, #5,

65

Chapter 2 hyperparameter OptimizatiOn

'l1\_size': 64, #1024,

'batch\_size': 512, #32,

'learning\_rate': 1e-2, #1e-4,

}

\# NNI HyperParameters

\# Run safely without NNI Experiment Context

nni\_hparams = nni.get\_next\_parameter()

hparams.update(nni\_hparams)

trial(hparams)

Remember that a trial script can be executed in stand-alone mode, so you can run a ch2/lenet\_hpo/pt\_trial.py to test its execution with custom parameters.

**Performing LeNet HPO Experiment**

And so now, we are all set for our first HPO study. Any real-world experiment can take several hours to several weeks, which is natural because each trial creates a unique model and training method. And the process of training can take quite a long time, depending on a model design and dataset. Some of the experiments in this book took quite a long time. Therefore, you can skip a complete experiment run or limit the number of trials with the maxTrialNumber setting. Keep in mind that if you run a limited experiment, your results may differ significantly from those presented in the book. For each experiment, I will give the time it took to complete it on a specific machine. We need to configure the NNI experiment and run it. Listin[g 2-13](#index_split_000.html#p79) contains the configuration for the LeNet HPO Experiment.

***Listing 2-13.*** LeNet HPO Experiment configuration. ch2/lenet\_hpo/config.yml trialConcurrency: 4

searchSpaceFile: search\_space.json

trialCodeDirectory: .

Uncomment PyTorch trial line to run the experiment using PyTorch implementation: trialCommand: python3 tf\_trial.py

#trialCommand: python3 pt\_trial.py

66

Chapter 2 hyperparameter OptimizatiOn

The search space contains 35 = 243 elements. This is a small search space, and we can use the Grid Search Tuner here:

tuner:

name: GridSearch

trainingService:

platform: local

The experiment can be run as follows:

nnictl create --config ch2/lenet\_hpo/config.yml

**Note** Duration ~ 2 hours on intel Core i7 with CUDa (GeForce GtX 1050)

The experiment returned the following best trial hyperparameters:

• **learning\_rate**: 0.001

• **batch\_size**:

256

• **l1\_size**:

64

• **kernel\_size**:

5

• **filter\_size**:

32

The best trial showed a **0.9885** result. And this is an acceptable outcome. We can assume that LeNet supplied by best hyperparameters recognizes handwritten numbers with 98.85% accuracy on test dataset.

In Figur[e 2-12](#index_split_000.html#p81), we can observe the top 1% of the top trials in the hyperparameters panel.

67

![](index-81_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-12.** Hyperparameter panel of LeNet HPO top 1% trials*

Figur[e 2-12 demons](#index_split_000.html#p81)trates that all the best results have kernel\_size = 5. Otherwise, the best results have no dependencies among its hyperparameters.

After completing a study, I like to visualize the results. We already have accuracy metric. But it will still be interesting to glance at the images that the LeNet model could not classify correctly. Perhaps the achieved accuracy of 98.85% is the best possible accuracy? Maybe the test dataset contains samples that cannot be correctly classified?

Listin[g 2-14 dis](#index_split_000.html#p81)plays the first nine failed predictions.

We import necessary modules:

***Listing 2-14.*** LeNet failed predictions. ch2/lenet\_hpo/display\_mnist\_failed\_

predictions.py

from math import floor

import numpy as np

from ch2.lenet\_hpo.tf\_lenet\_model import TfLeNetModel

import matplotlib.pyplot as plt

import tensorflow as tf

from ch2.utils.datasets import mnist\_dataset

LeNet model is initialized using best layer hyperparameters:

\# Best Hyperparameters

hparams = {

"learning\_rate": 0.001,

"batch\_size": 256,

68

Chapter 2 hyperparameter OptimizatiOn

"l1\_size": 64,

"kernel\_size": 5,

"filter\_size": 32

}

\# Making this script Reproducible

tf.random.set\_seed(1)

\# Initializing LeNet Model

model = TfLeNetModel(

filter\_size = hparams\['filter\_size'\],

kernel\_size = hparams\['kernel\_size'\],

l1\_size = hparams\['l1\_size'\]

)

And after that, we train the model using the best training hyperparameters:

\# Model Training

model.train(

batch\_size = hparams\['batch\_size'\],

learning\_rate = hparams\['learning\_rate'\]

)

Trained model makes its predictions on test MNIST dataset:

\# MNIST Dataset

(\_, \_), (x\_test, y\_test) = mnist\_dataset()

\# Predictions

output = model(x\_test)

y\_pred = tf.argmax(output, 1)

Collecting the first nine failed predictions:

number\_of\_fails\_left = 9

fails = \[\]

for i in range(len(x\_test)):

if number\_of\_fails\_left == 0:

break

69

Chapter 2 hyperparameter OptimizatiOn

if y\_pred\[i\] != y\_test\[i\]:

fails.append((x\_test\[i\], (y\_pred\[i\], y\_test\[i\])))

number\_of\_fails\_left -= 1

Displaying failed predictions:

fig, axs = plt.subplots(3, 3)

for i in range(len(fails)):

sample, (pred, actual) = fails\[i\]

img = np.array(sample, dtype = 'float')

img = img \* 255

pixels = img.reshape((28, 28))

ax = axs\[floor(i / 3), i % 3\]

ax.set\_title(f'#{i+1}: {actual} ({pred})')

ax.set\_xticks(\[\])

ax.set\_yticks(\[\])

ax.imshow(pixels, cmap = 'gray')

plt.show()

Figur[e 2-13 dis](#index_split_000.html#p84)plays LeNet failed predictions. To be honest, the samples #1, #3, #4,

#5, #6, and #8 are really difficult to classify. I don’t think that a reader would recognize the number 2 in sample #4. Therefore, we do not need to demand 100% accuracy from our model. But still, I think there is room for improvement.

70

![](index-84_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-13.** LeNet failed predictions*

Congratulations! We have completed our first real-world study. We defined the

problem, chose the model frame (LeNet), expressed the search space, made model

implementations, and found the best hyperparameters for the problem. But this is only the beginning. Let’s continue the research and see what other exciting results we can achieve.

**Upgrading LeNet with ReLU and Dropout**

Libraries: TensorFlow (Keras API), PyTorch

Experienced data scientists may have the question: Hey?! Why didn’t we use the

dropout layer and rectified linear unit (ReLU) as the activation function for LeNet model in the previous section? Because the original LeNet model did not use the ReLU

activation. And the dropout technique was first introduced in 2012, 22 years after creating the LeNet architecture. One of the main problems with the LeNet concept was that it used sigmoid as an activation function. The sigmoid activation function led to slower training and a vanishing gradient problem. The dropout technique is also one of the most popular regularization methods. Nowadays, we cannot imagine a successful pattern recognition model that does not use ReLU and dropout layers. Let’s pretend that we have never heard anything about ReLU and dropout, and someone advises us 71

![](index-85_1.png)

Chapter 2 hyperparameter OptimizatiOn

to inject these techniques into a LeNet model to improve its performance. We can do research using HPO that will help us find the best architecture.

Let’s introduce an activation design hyperparameter responsible for choosing the activation function. To simplify the problem, we will use a one-for-all policy. This means that if the activation hyperparameter has a sigmoid value, then the LeNet model will have a sigmoid function for all activations. The same is true if activation has a relu value. Figur[e 2-14](#index_split_000.html#p85) presents activation hyperparameter.

***Figure 2-14.** Activation design hyperparameter*

Typically, a dropout layer is inserted between linear layers. But we initially do not know whether this technique would be effective, so we have to make possible two

variants of LeNet architecture: with dropout layer and without dropout layer. To do this, we use the use\_dropout design hyperparameter. If use\_dropout is 0, then the LeNet model does not use the dropout layer, and if use\_dropout is 1, then the LeNet model uses the dropout layer. At the same time, the dropout layer will be tested using three different *p* (dropout rate) values: 0.3, 0.5, and 0.7. Figur[e 2-15 pr](#index_split_000.html#p86)esents use\_dropout design hyperparameter.

72

![](index-86_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-15.** Dropout design hyperparameter*

Each model design works well with specific layer hyperparameters. Therefore, we

also need to include layer hyperparameters in the search space. In this experiment, we will use the same hyperparameters we used in the previous section. But we will choose slightly different values for them:

• filter\_size: 16, 32

• kernel\_size: 5, 7

• l1\_size: 64, 128, 256

• batch\_size: 512, 1024

• learning\_rate: 0.001, 0.0001

Listin[g 2-15 pr](#index_split_000.html#p87)esents hyperparameter constraints we made earlier as NNI search space.

73

Chapter 2 hyperparameter OptimizatiOn

***Listing 2-15.*** LeNet Upgrade HPO search space. ch2/lenet\_upgrade/search\_

space.json

{

"activation": {

"\_type": "choice", "\_value": \["sigmoid", "relu"\]}, Here, we use nested choice method to implement use\_dropout hyperparameter:

"use\_dropout": {

"\_type": "choice",

"\_value": \[

{"\_name": 0},

{

"\_name": 1, "rate":

{"\_type": "choice", "\_value": \[0.3, 0.5, 0.7\]}

}

\]

},

"filter\_size": {

"\_type": "choice", "\_value": \[16, 32\]},

"kernel\_size": {

"\_type": "choice", "\_value": \[5, 7\]},

"l1\_size": {

"\_type": "choice", "\_value": \[64, 128, 256\]},

"batch\_size": {

"\_type": "choice", "\_value": \[512, 1024\]},

"learning\_rate": {

"\_type": "choice", "\_value": \[0.001, 0.0001\]}

}

And just like in the previous section, the next step is to make TensorFlow and

PyTorch implementations of the LeNet Upgrade model.

74

Chapter 2 hyperparameter OptimizatiOn

**TensorFlow LeNet Upgrade Implementation**

In this section, we will examine the LeNet Upgrade model’s implementation using

TensorFlow (Keras API).

We will examine only \_\_init\_\_ and call methods in TfLeNetUpgradeModel.

Other methods are the same as in TfLeNetModel (ch2/lenet\_hpo/tf\_lenet\_model.py).

Listing [2-16 sho](#index_split_000.html#p88)ws the LeNet Upgrade model with six hyperparameters.

***Listing 2-16.*** LeNet Upgrade. TensorFlow implementation. ch2/lenet\_upgrade/

tf\_lenet\_upgrade\_model.py

class TfLeNetUpgradeModel(Model):

def \_\_init\_\_(

self,

filter\_size,

kernel\_size,

l1\_size,

activation,

use\_dropout,

dropout\_rate = None

):

super().\_\_init\_\_()

First layer stack with activation variable:

self.conv1 = Conv2D(

filters = filter\_size,

kernel\_size = kernel\_size,

activation = activation

)

self.pool1 = MaxPool2D(pool\_size = 2)

self.conv2 = Conv2D(

filters = filter\_size \* 2,

kernel\_size = kernel\_size,

activation = activation

)

75

Chapter 2 hyperparameter OptimizatiOn

self.pool2 = MaxPool2D(pool\_size = 2)

self.flatten = Flatten()

self.fc1 = Dense(

units = l1\_size,

activation = activation

)

We add dropout layer if use\_dropout and identity layer otherwise:

if use\_dropout:

self.drop = Dropout(rate = dropout\_rate)

else:

self.drop = tf.identity

Final linear layer stack:

self.fc2 = Dense(

units = 10,

activation = 'softmax'

)

LeNet Upgrade model invokes each layer sequentially:

def call(self, x, \*\*kwargs):

x = self.conv1(x)

x = self.pool1(x)

x = self.conv2(x)

x = self.pool2(x)

x = self.flatten(x)

x = self.fc1(x)

x = self.drop(x)

return self.fc2(x)

And after implementing LeNetUpgradeModel, we can implement the NNI trial

script using Listin[g 2-17.](#index_split_000.html#p90)

We import necessary modules and pass code root directory to system path:

76

Chapter 2 hyperparameter OptimizatiOn

***Listing 2-17.*** NNI trial script with TensorFlow LeNetUpgrade implementation.

ch2/lenet\_upgrade/tf\_trial.py

import os

import sys

import nni

\# We use relative import for user-defined modules

SCRIPT\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_)) + '/../..'

sys.path.append(SCRIPT\_DIR)

from ch2.lenet\_upgrade.tf\_lenet\_upgrade\_model import TfLeNetUpgradeModel

The trial method initializes the model, trains it, tests it, and returns the NNI metric: def trial(hparams):

use\_dropout = bool(hparams\['use\_dropout'\]\['\_name'\])

model\_params = {

"filter\_size": hparams\['filter\_size'\],

"kernel\_size": hparams\['kernel\_size'\],

"l1\_size": hparams\['l1\_size'\],

"activation": hparams\['activation'\],

"use\_dropout": use\_dropout

}

if use\_dropout:

model\_params\['dropout\_rate'\] = hparams\['use\_dropout'\]\['rate'\]

model = TfLeNetUpgradeModel(\*\*model\_params)

model.train(

batch\_size = hparams\['batch\_size'\],

learning\_rate = hparams\['learning\_rate'\]

)

accuracy = model.test()

\# send final accuracy to NNI

nni.report\_final\_result(accuracy)

77

Chapter 2 hyperparameter OptimizatiOn

Next, we define the main entry point for the trial:

if \_\_name\_\_ == '\_\_main\_\_':

\# Manual HyperParameters

hparams = {

'use\_dropout': {'\_name': 1, 'rate': 0.5},

'activation': 'relu',

'filter\_size': 32,

'kernel\_size': 3,

'l1\_size': 64,

'batch\_size': 512,

'learning\_rate': 1e-3,

}

\# NNI HyperParameters

\# Run safely without NNI Experiment Context

nni\_hparams = nni.get\_next\_parameter()

hparams.update(nni\_hparams)

trial(hparams)

Remember that a trial script can be executed in stand-alone mode, so you can run a ch2/lenet\_upgrade/tf\_trial.py to test its execution with custom parameters.

**PyTorch LeNet Upgrade Implementation**

In this section, we will examine the LeNet Upgrade model’s implementation using

PyTorch.

We will examine only \_\_init\_\_ and forward methods in PtLeNetUpgradeModel.

Other methods are the same as in PtLeNetModel (ch2/lenet\_hpo/pt\_lenet\_model.py).

Listin[g 2-18 sho](#index_split_000.html#p92)ws the LeNet Upgrade model with six hyperparameters: 78

Chapter 2 hyperparameter OptimizatiOn

***Listing 2-18.*** LeNet Upgrade. PyTorch implementation. ch2/lenet\_upgrade/

pt\_lenet\_upgrade\_model.py

class PtLeNetUpgradeModel(nn.Module):

def \_\_init\_\_(

self,

filter\_size,

kernel\_size,

l1\_size,

activation,

use\_dropout,

dropout\_rate = None

):

super(PtLeNetUpgradeModel, self).\_\_init\_\_()

We set self.act layer by activation variable:

\# Activation Function

if activation == 'relu':

self.act = torch.relu

elif activation == 'sigmoid':

self.act = torch.sigmoid

else:

raise Exception(f'Unknown activation: {activation}')

We add dropout layer if use\_dropout and identity layer otherwise:

if use\_dropout:

self.drop = nn.Dropout(p = dropout\_rate)

else:

self.drop = nn.Identity()

Next, we set other LeNet layers:

\# Saving l1\_size HyperParameter

self.l1\_size = l1\_size

79

Chapter 2 hyperparameter OptimizatiOn

self.conv1 = nn.Conv2d(

1,

filter\_size,

kernel\_size = kernel\_size

)

self.conv2 = nn.Conv2d(

filter\_size,

filter\_size \* 2,

kernel\_size = kernel\_size

)

\# Lazy fc1 Layer Initialization

self.fc1\_\_in\_features = 0

self.\_fc1 = None

self.fc2 = nn.Linear(l1\_size, 10)

LeNet Upgrade model invokes each layer sequentially:

def forward(self, x):

x = self.act(self.conv1(x))

x = F.max\_pool2d(x, 2, 2)

x = self.act(self.conv2(x))

x = F.max\_pool2d(x, 2, 2)

\# Flatting all dimensions but batch-dimension

self.fc1\_\_in\_features = np.prod(x.shape\[1:\])

x = x.view(-1, self.fc1\_\_in\_features)

x = self.act(self.fc1(x))

x = self.drop(x)

x = self.fc2(x)

return F.log\_softmax(x, dim = 1)

And after implementing LeNetUpgradeModel, we can implement the NNI trial

script using Listin[g 2-19.](#index_split_000.html#p94)

We import necessary modules and pass code root directory to system path:

80

Chapter 2 hyperparameter OptimizatiOn

***Listing 2-19.*** NNI trial script with PyTorch LeNetUpgrade implementation. ch2/

lenet\_upgrade/pt\_trial.py

import os

import sys

import nni

\# We use relative import for user-defined modules

SCRIPT\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_)) + '/../..'

sys.path.append(SCRIPT\_DIR)

from ch2.lenet\_upgrade.pt\_lenet\_upgrade\_model import PtLeNetUpgradeModel

The trial method initializes the model, trains it, tests it, and returns the NNI metric: def trial(hparams):

use\_dropout = bool(hparams\['dropout'\]\['\_name'\])

model\_params = {

"filter\_size": hparams\['filter\_size'\],

"kernel\_size": hparams\['kernel\_size'\],

"l1\_size": hparams\['l1\_size'\],

"activation": hparams\['activation'\],

"use\_dropout": use\_dropout

}

if use\_dropout:

model\_params\['dropout\_rate'\] = hparams\['dropout'\]\['rate'\]

model = PtLeNetUpgradeModel(\*\*model\_params)

model.train\_model(

batch\_size = hparams\['batch\_size'\],

learning\_rate = hparams\['learning\_rate'\]

)

accuracy = model.test\_model()

nni.report\_final\_result(accuracy)

81

Chapter 2 hyperparameter OptimizatiOn

Next, we define the main entry point for the trial:

if \_\_name\_\_ == '\_\_main\_\_':

\# Manual HyperParameters

hparams = {

'dropout': {'\_name': 1, 'rate': 0.5},

'activation': 'relu',

'filter\_size': 32,

'kernel\_size': 3,

'l1\_size': 64,

'batch\_size': 512,

'learning\_rate': 1e-3,

}

\# NNI HyperParameters

\# Run safely without NNI Experiment Context

nni\_hparams = nni.get\_next\_parameter()

hparams.update(nni\_hparams)

trial(hparams)

Remember that a trial script can be executed in stand-alone mode, so you can run a ch2/lenet\_upgrade/pt\_trial.py to test its execution with custom parameters.

**Performing LeNet Upgrade HPO Experiment**

We are now ready to run our second experiment. We can consider this experiment

as a battle between Vanilla LeNet model and LeNet enhanced by ReLU and dropout.

Please be aware that the results of this study will be specific to the MNIST problem. An experiment launched on a different dataset can lead to completely different results.

Listin[g 2-20 defines the confi](#index_split_000.html#p95)guration of the LeNet Upgrade experiment.

***Listing 2-20.*** LeNet Upgrade HPO Experiment configuration. ch2/lenet\_

upgrade/config.yml

trialConcurrency: 2

82

Chapter 2 hyperparameter OptimizatiOn

We will limit the number of trials:

maxTrialNumber: 300

searchSpaceFile: search\_space.json

trialCodeDirectory: .

Uncomment PyTorch trial line to run the experiment using PyTorch implementation: trialCommand: python3 tf\_trial.py

#trialCommand: python3 pt\_trial.py

GridSearch Tuner cannot be used for search spaces that utilize nested choice, so we pick Random Search Tuner:

tuner:

name: Random

trainingService:

platform: local

The experiment can be run as follows:

nnictl create --config ch2/lenet\_upgrade/config.yml

**Note** Duration ~ 3 hours on intel Core i7 with CUDa (GeForce GtX 1050)

The experiment returned the following best trial hyperparameters:

• **activation**: relu

• **use\_dropout**: 1

• **rate**: 0.5

• **filter\_size**: 32

• **kernel\_size**: 5

• **l1\_size**: 256

• **batch\_size**: 512

• **learning\_rate**: 0.001

83

![](index-97_1.png)

Chapter 2 hyperparameter OptimizatiOn

The best trial demonstrated a **0.9923** result, which is a significant improvement over the 0.9885 we got in the previous section. We see that the best hyperparameter combination uses ReLU activation and dropout (p=0.5) layer. Could this mean that LeNet empowered by ReLU and dropout won this battle? Let’s look at the top 1% trials in the hyperparameter panel (Figure [2-16](#index_split_000.html#p97)) to answer this question.

***Figure 2-16.** Hyperparameter panel of LeNet Upgrade HPO top 1% trials*

Figur[e 2-16 demons](#index_split_000.html#p97)trates that all three best hyperparameter combinations have the following hyperparameter values:

• **activation**: relu

• **use\_dropout**: 1

which can be considered as solid evidence in favor of using the ReLU and dropout techniques. Of course, this result may seem somewhat obvious, but this is only because you already know about the benefits of using ReLU and dropout layers. Initially, this fact did not seem so obvious and required practical evidence, which we have just demonstrated.

Finally, let’s take a look at the MNIST database samples that the upgraded LeNet model failed to classify. These samples are presented in Figur[e 2-17.](#index_split_000.html#p98)

84

![](index-98_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-17.** Upgraded LeNet model fails*

I deliberately didn’t print the correct results in Figure [2-17. T](#index_split_000.html#p98)ake one minute, write down your answer for each sample, and compare it with the correct answers in the following:

*Answers. #1: 9. #2: 7. #3: 7. #4: 0. #5: 2. #6: 8. #7: 2. #8: 9. #9. 8*

If you haven’t made a single mistake, then I admire you! I guessed only four

numbers. If a human has difficulties recognizing some handwritten characters, then the neural network is already close to its performance threshold. The current result of the upgraded LeNet model we have developed is close to the best.

This section demonstrates how new deep learning techniques can be injected into

existing architecture. We defined a search space to choose the best design combination.

HPO chose an upgraded model design that significantly improved the performance of the original model. And this is a very simple and useful technique that will allow you to uptune your models using the latest advances in machine learning.

**From LeNet to AlexNet**

Libraries: TensorFlow (Keras API), PyTorch (PyTorch Lightning)

Well, handwriting recognition is a rather important task, but it seems that it’s time to move on to more complicated problems. Let’s try to classify more complex objects.

How about developing a model that will classify humans and horses? Figur[e 2-18](#index_split_000.html#p99) shows 85

![](index-99_1.png)

Chapter 2 hyperparameter OptimizatiOn

samples of “humans or horses” dataset. This dataset contains 300×300 color images, that is, (300, 300, 3) tensors. Obviously, the image of a human or a horse is more complex than a 28×28 grayscale image of a handwritten number. And perhaps, we will need to evolve the LeNet model that we considered earlier. We will call it *LeNet Evolution* model.

***Figure 2-18.** Humans vs. horses dataset*

Let’s look at the architecture of the LeNet model again. LeNet model design can

be divided into two components: *feature extraction* and *decision making*. Indeed, the convolution layer stack ( *Conv2D* → *Activation* → *MaxPool2D* → *Conv2D* → *Activation*

→ *MaxPool2D* → *Flatten*) is responsible for extracting image patterns, that is, feature extraction. At the same time, the fully connected layer stack ( *Linear* → *Activation* → 

*Linear* → *SoftMax*) is responsible for selecting particular patterns to classify an input object. Figur[e 2-19 sho](#index_split_000.html#p100)ws the areas of responsibility for each component.

86

![](index-100_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-19.** Feature extraction and decision maker components*

Since human and horse images are more complex, we need to make the feature

extraction component more sophisticated. Two types of layer sequences are usually responsible for extracting image patterns: *Conv2D* → *Activation* → *MaxPool2D* and *Conv2D* → *Activation*. We can build an experiment that will inject different feature extraction sequences to find the best model design to solve the “human and horses”

classification problem. In the following, we define three types of feature extraction layer sequences adding none as an empty sequence:

87

Chapter 2 hyperparameter OptimizatiOn

• **simple**: *Conv2D* → *Activation*

• **with\_pool**: *Conv2D* → *Activation* → *MaxPool2D*

• **none**: Identity layer

Each feature extraction sequence will have additional layer hyperparameters:

filters, kernel, pool\_size.

Let the LeNet Evolution model have three pattern extraction slots. Each of these slots can be filled with one of the feature extraction sequences: simple, with\_pool, none. For example, a LeNet Evolution model can have three feature extraction slots filled with the following layer sequences:

• **with\_pool**: *Conv2D(kernel\_size=5,* *filters=16)* → *Activation* → 

*MaxPool2D(pool\_size=3)*

• **none**: Identity

• **simple**: *Conv2D(kernel\_size=3,* *filters=8)*→ *Activation* And finally, the LeNet Evolution feature extraction component will look the following way: *Conv2D(kernel\_size=5,* *filters=16)* → *Activation* → *MaxPool2D(pool\_size=3)*

→ *Conv2D(kernel\_size=3,* *filters=8)* → *Activation*.

We can consider feature extraction sequences as the building blocks of the LeNet Evolution model, as shown in Figur[e 2-20](#index_split_000.html#p102).

88

![](index-102_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-20.** LeNet Evolution feature extraction component*

And so we can define the three design hyperparameters of the LeNet Evolution

model. Ta[ble 2-4 pr](#index_split_000.html#p102)ovides LeNet Evolution model design hyperparameters.

***Table 2-4.** LeNet Evolution feature extraction hyperparameters*

**Name**

**Description**

**Values**

fe\_slot\_1

Feature extraction Sequence 1

• none

• simple

• filters: 8, 16, 32

• kernel: 5, 7, 9, 11

• with\_pool:

• filters: 8, 16, 32

• kernel: 5, 7, 9, 11

• pool\_size: 3, 5, 7

( *continued*)

89

Chapter 2 hyperparameter OptimizatiOn

***Table 2-4.*** ( *continued*)

**Name**

**Description**

**Values**

fe\_slot\_2

Feature extraction Sequence 2

• none

• simple

• filters: 8, 16, 32

• kernel: 5, 7, 9, 11

• with\_pool:

• filters: 8, 16, 32

• kernel: 5, 7, 9, 11

• pool\_size: 3, 5, 7

fe\_slot\_3

Feature extraction Sequence 3

• none

• simple

• filters: 8, 16, 32

• kernel: 5, 7, 9, 11

• with\_pool:

• filters: 8, 16, 32

• kernel: 5, 7, 9, 11

• pool\_size: 3, 5, 7

Since the feature extraction component of the LeNet Evolution model returns more features than it did with the MNIST problem, we should also let the experiment create a more advanced decision maker component. The decision maker component can be

improved by adding an extra linear layer. This is the easiest and most efficient way to enhance a decision maker component. Since we proved the sustainability of the dropout layer and ReLU activation in the previous section, they will also be used in the decision maker component. Figur[e 2-21](#index_split_000.html#p104) demonstrates two variants of the decision maker component.

90

![](index-104_1.png)

Chapter 2 hyperparameter OptimizatiOn

***Figure 2-21.** LeNet Evolution decision maker component*

The design of the decision maker component will be determined by the following

hyperparameters shown in Table [2-5](#index_split_000.html#p104).

***Table 2-5.** LeNet Evolution decision maker hyperparameters*

**Name**

**Description**

**Values**

l1\_size

Output size of first linear layer

512, 1024, 2048

l2\_size

Output size of second linear layer

0, 512, 1024

if 0 value is chosen, then the

second linear layer is skipped

dropout\_rate

Dropout probability of dropout layers

0.3, 0.5, 0.7

Also, we will use learning\_rate as a training hyperparameter with the following

options: 0.001, 0.0001.

91

Chapter 2 hyperparameter OptimizatiOn

In this experiment, we are not just looking for the best hyperparameters, but we are trying to create a new architecture of the deep learning model based on the principles of the original LeNet model. Here, we try not just to tune an existing model but also to create a new one. The list of design hyperparameters is responsible for unique deep learning model design.

Listin[g 2-21 defines NNI s](#index_split_000.html#p105)earch space of the LeNet Evolution model.

The first feature slot fe\_slot\_1 can be filled with one of these feature extraction sequences:

• *Conv2D*(kernel\_size, filters) → *Activation* → 

*MaxPool2D*(pool\_size)

• *Conv2D*(kernel\_size, filters) → *Activation*

• *None*

***Listing 2-21.*** LeNet Evolution HPO search space. ch2/lenet\_to\_alexnet/

search\_space.json

{

"fe\_slot\_1": {

"\_type": "choice",

"\_value": \[

{"\_name": "none"},

{

"\_name": "simple",

"filters": {"\_type": "choice", "\_value": \[8, 16, 32\]},

"kernel": {"\_type": "choice", "\_value": \[5, 7, 9, 11\]}

},

{

"\_name": "with\_pool",

"filters": {"\_type": "choice", "\_value": \[8, 16, 32\]},

"kernel": {"\_type": "choice", "\_value": \[5, 7, 9, 11\]},

"pool\_size": {"\_type": "choice", "\_value": \[3, 5, 7\]}

}

\]

},

92

Chapter 2 hyperparameter OptimizatiOn

The second and third feature extraction slots (fe\_slot\_2, fe\_slot\_3) have the

same values set as fe\_slot\_1:

"fe\_slot\_2": {

"\_type": "choice",

"\_value": \[

{"\_name": "none"},

{

"\_name": "simple",

"filters": {"\_type": "choice", "\_value": \[8, 16, 32\]},

"kernel": {"\_type": "choice", "\_value": \[5, 7, 9, 11\]}

},

{

"\_name": "with\_pool",

"filters": {"\_type": "choice", "\_value": \[8, 16, 32\]},

"kernel": {"\_type": "choice", "\_value": \[5, 7, 9, 11\]},

"pool\_size": {"\_type": "choice", "\_value": \[3, 5, 7\]}

}

\]

},

"fe\_slot\_3": {

"\_type": "choice",

"\_value": \[

{"\_name": "none"},

{

"\_name": "simple",

"filters": {"\_type": "choice", "\_value": \[8, 16, 32\]},

"kernel": {"\_type": "choice", "\_value": \[5, 7, 9, 11\]}

},

{

"\_name": "with\_pool",

"filters": {"\_type": "choice", "\_value": \[8, 16, 32\]},

"kernel": {"\_type": "choice", "\_value": \[5, 7, 9, 11\]},

"pool\_size": {"\_type": "choice", "\_value": \[3, 5, 7\]}

}

\]

},

93

Chapter 2 hyperparameter OptimizatiOn

Next, we define decision maker hyperparameters:

"l1\_size": {

"\_type": "choice", "\_value": \[512, 1024, 2048\]},

"l2\_size": {

"\_type": "choice", "\_value": \[0, 512, 1024\]},

"dropout\_rate": {

"\_type": "choice", "\_value": \[0.3, 0.5, 0.7\]},

And learning\_rate hyperparameter finishes the search space:

"learning\_rate": {

"\_type": "choice", "\_value": \[0.001, 0.0001\]}

}

We have just defined rather nontrivial search space. Let’s hope that the result of the experiment will meet our expectations and the resulting architecture will perfectly solve the problem of human and horses classification. The next step is to make TensorFlow and PyTorch implementations of the LeNet Evolution model.

**TensorFlow LeNet Evolution Implementation**

Listin[g 2-22 pr](#index_split_001.html#p107)esents the **LeNet Evolution** model’s implementation using TensorFlow.

We import necessary modules:

***Listing 2-22.*** LeNet Upgrade. TensorFlow implementation. ch2/lenet\_to\_

alexnet/tf\_lenet\_evolution.py

import tensorflow as tf

from tensorflow.keras import Model

from tensorflow.keras.layers import (

Conv2D, Dense,

Dropout, Flatten, MaxPool2D, ReLU,

)

from tensorflow.keras.optimizers import Adam

from ch2.utils.datasets import hoh\_dataset

from ch2.utils.tf\_utils import TfNniIntermediateResult

94

Chapter 2 hyperparameter OptimizatiOn

LeNet Evolution model is initialized with four hyperparameters:

class TfLeNetEvolution(Model):

def \_\_init\_\_(

self,

feat\_ext\_sequences,

l1\_size,

l2\_size,

dropout\_rate

):

super().\_\_init\_\_()

Model’s layer stack is filled dynamically depending on hyperparameters:

layer\_stack = \[\]

First, we define feature extraction sequences:

for fe\_seq in feat\_ext\_sequences:

if fe\_seq\['type'\] in \['simple', 'with\_pool'\]:

\# Constructing Feature Extraction Sequence

layer\_stack.append(

Conv2D(

filters = fe\_seq\['filters'\],

kernel\_size = fe\_seq\['kernel'\]

)

)

if fe\_seq\['type'\] == 'with\_pool':

layer\_stack.append(

MaxPool2D(

pool\_size = fe\_seq\['pool\_size'\]

)

)

layer\_stack.append(ReLU())

layer\_stack.append(Flatten())

95

Chapter 2 hyperparameter OptimizatiOn

Next, we construct decision maker component:

layer\_stack.append(

Dense(

units = l1\_size,

activation = 'relu'

)

)

layer\_stack.append(

Dropout(rate = dropout\_rate)

)

Additional linear layer is added if l2\_size is greater than zero:

\# Optional Linear Layer

if l2\_size > 0:

layer\_stack.append(

Dense(

units = l2\_size,

activation = 'relu'

)

)

layer\_stack.append(

Dropout(rate = dropout\_rate)

)

Final classification layer:

layer\_stack.append(

Dense(

units = 2,

activation = 'softmax'

)

)

And here, we set layer sequence to the model:

self.seq = tf.keras.Sequential(layer\_stack)

96

Chapter 2 hyperparameter OptimizatiOn

Model execution method is trivial sequence layer call:

def call(self, x, \*\*kwargs):

y = self.seq(x)

return y

As before, we use the Adam optimizer with cross-entropy as the loss function:

def train(self, learning\_rate, batch\_size, epochs):

self.compile(

optimizer = Adam(learning\_rate = learning\_rate),

loss = 'sparse\_categorical\_crossentropy',

metrics = \['accuracy'\]

)

(x\_train, y\_train), \_ = hoh\_dataset()

intermediate\_cb = TfNniIntermediateResult('accuracy')

self.fit(

x\_train,

y\_train,

batch\_size = batch\_size,

epochs = epochs,

verbose = 0,

callbacks = \[intermediate\_cb\]

)

Model testing:

def test(self):

(\_, \_), (x\_test, y\_test) = hoh\_dataset()

loss, accuracy = self.evaluate(x\_test, y\_test, verbose = 0)

return accuracy

Since LeNetEvolutionModel is done, we can implement the NNI trial script using

Listin[g 2-23.](#index_split_001.html#p111)

97

Chapter 2 hyperparameter OptimizatiOn

We import necessary modules and pass code root directory to system path:

***Listing 2-23.*** NNI trial script with TensorFlow LeNetEvolution implementation.

ch2/lenet\_to\_alexnet/tf\_trial.py

import os

import sys

import nni

\# We use relative import for user-defined modules

\# For NNI use relative import for user-defined modules

SCRIPT\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_)) + '/../..'

sys.path.append(SCRIPT\_DIR)

from ch2.lenet\_to\_alexnet.tf\_lenet\_evolution import TfLeNetEvolution

The trial method initializes the model, trains it, tests it, and returns the NNI metric: def trial(hparams):

Feature extraction hyperparameters are converted to universal form:

feat\_ext\_sequences = \[\]

for k, v in hparams.items():

if k.startswith('fe\_slot\_'):

v\['type'\] = v\['\_name'\]

feat\_ext\_sequences.append(v)

Model initialization:

model = TfLeNetEvolution(

feat\_ext\_sequences = feat\_ext\_sequences,

l1\_size = hparams\['l1\_size'\],

l2\_size = hparams\['l2\_size'\],

dropout\_rate = hparams\['dropout\_rate'\]

)

98

Chapter 2 hyperparameter OptimizatiOn

Here, we train the model during 50 epochs and fixed batch\_size = 16:

model.train(

batch\_size = 16,

learning\_rate = 0.001,

epochs = 50

)

Testing the model:

accuracy = model.test()

And after, we return accuracy metric to NNI tuner:

\# send final accuracy to NNI

nni.report\_final\_result(accuracy)

Next, we define the main entry point for the trial:

if \_\_name\_\_ == '\_\_main\_\_':

\# Manual HyperParameters

hparams = {

'fe\_slot\_1': {

'\_name': 'simple',

'filters': 16,

'kernel': 7

},

'fe\_slot\_2': {

'\_name': 'with\_pool',

'filters': 8,

'kernel': 5,

'pool\_size': 5

},

'fe\_slot\_3': {

'\_name': 'with\_pool',

'filters': 8,

'kernel': 5,

'pool\_size': 3

},

99

Chapter 2 hyperparameter OptimizatiOn

'l1\_size': 1024,

'l2\_size': 512,

'dropout\_rate': .3,

'learning\_rate': 0.001

}

\# NNI HyperParameters

\# Run safely without NNI Experiment Context

nni\_hparams = nni.get\_next\_parameter()

hparams.update(nni\_hparams)

trial(hparams)

Remember that a trial script can be executed in stand–alone mode, so you can run a ch2/lenet\_to\_alexnet/tf\_trial.py to test its execution with custom parameters.

**PyTorch LeNet Evolution Implementation**

Section, we will examine the **LeNet Evolution** model’s implementation using PyTorch Lightning. PyTorch Lightning is a seamless PyTorch wrapper that helps eliminate the PyTorch code boilerplate. It is more concise and better suited for such tasks. Listin[g 2-24](#index_split_001.html#p113)

demonstrates the LeNet Evolution model based on PyTorch Lightning.

We import necessary modules:

***Listing 2-24.*** LeNet Evolution. PyTorch Lightning implementation. ch2/lenet\_

to\_alexnet/pt\_lenet\_evolution.py

import nni

import torch

import torch.nn.functional as F

import pytorch\_lightning as pl

from sklearn.metrics import accuracy\_score

from torch import nn

import numpy as np

from torch.utils.data import DataLoader

from ch2.utils.datasets import hoh\_dataset

from ch2.utils.pt\_utils import SimpleDataset

100

Chapter 2 hyperparameter OptimizatiOn

LeNet Evolution model is initialized with all five hyperparameters. PyTorch

Lightning model encapsulates initialization and training logic in the same class, so we pass all hyperparameters at once:

class PtLeNetEvolution(pl.LightningModule):

def \_\_init\_\_(

self,

feat\_ext\_sequences,

l1\_size,

l2\_size,

dropout\_rate,

learning\_rate

) -> None:

super().\_\_init\_\_()

learning\_rate and dropout\_rate hyperparameters are stored explicitly:

self.lr = learning\_rate

self.dropout\_rate = dropout\_rate

self.save\_hyperparameters()

The first step is to create a layer sequence for the feature extraction component dynamically:

fe\_stack = \[\]

\# Input size of next conv layer is out\_channels of previous one

in\_dim = 3

for fe\_seq in feat\_ext\_sequences:

if fe\_seq\['type'\] in \['simple', 'with\_pool'\]:

fe\_stack.append(

nn.Conv2d(

in\_dim,

out\_channels = fe\_seq\['filters'\],

kernel\_size = fe\_seq\['kernel'\],

bias = False

)

101

Chapter 2 hyperparameter OptimizatiOn

)

if fe\_seq\['type'\] == 'with\_pool':

fe\_stack.append(

nn.MaxPool2d(

kernel\_size = fe\_seq\['pool\_size'\]

)

)

fe\_stack.append(nn.ReLU())

in\_dim = fe\_seq\['filters'\]

self.fe\_stack = nn.Sequential(\*fe\_stack)

The next step is to create a layer sequence for the decision maker component:

\# Lazy fc1 Layer Initialization

self.fc1\_\_in\_features = 0

self.\_fc1 = None

Additional linear layer is added if l2\_size is greater than zero:

if l2\_size > 0:

self.fc2 = nn.Sequential(

nn.Linear(l1\_size, l2\_size),

nn.ReLU(),

nn.Dropout(dropout\_rate)

)

self.fc3 = nn.Linear(l2\_size, 2)

else:

self.fc2 = nn.Identity()

self.fc3 = nn.Linear(l1\_size, 2)

Here, we again utilize the familiar lazy layer initialization pattern:

@property

def fc1(self):

if self.\_fc1 is None:

self.\_fc1 = nn.Sequential(

nn.Linear(

self.fc1\_\_in\_features,

102

Chapter 2 hyperparameter OptimizatiOn

self.hparams\['l1\_size'\]

),

nn.ReLU(),

nn.Dropout(self.dropout\_rate)

)

return self.\_fc1

Model execution method:

def forward(self, x):

\# calling feature extraction layer sequence

x = self.fe\_stack(x)

\# Flatting all dimensions but batch-dimension

self.fc1\_\_in\_features = np.prod(x.shape\[1:\])

x = x.view(-1, self.fc1\_\_in\_features)

x = self.fc1(x)

x = self.fc2(x)

x = self.fc3(x)

return F.log\_softmax(x, dim = 1)

We use the Adam optimizer with the learning\_rate hyperparameter:

def configure\_optimizers(self):

return torch.optim.Adam(

self.parameters(),

lr = self.lr

)

Training and test methods use cross-entropy loss function:

def training\_step(self, batch, batch\_idx):

x, y = batch

p = self(x)

loss = F.cross\_entropy(p, y)

self.log("train\_loss", loss, prog\_bar = True)

nni.report\_intermediate\_result(loss.item())

return loss

103

Chapter 2 hyperparameter OptimizatiOn

def test\_step(self, batch, batch\_idx):

x, y = batch

p = self(x)

loss = F.cross\_entropy(p, y)

self.log('test\_loss', loss, prog\_bar = True)

return loss

The following method performs the training process on the training dataset and tests the trained model on the test dataset:

def train\_and\_test\_model(self, batch\_size, epochs):

Training and testing datasets are prepared:

(x\_train, y\_train), (x\_test, y\_test) = hoh\_dataset()

x\_train = torch.from\_numpy(x\_train).float()

y\_train = torch.from\_numpy(y\_train).long()

x\_test = torch.from\_numpy(x\_test).float()

y\_test = torch.from\_numpy(y\_test).long()

x\_train = torch.permute(x\_train, (0, 3, 1, 2))

x\_test = torch.permute(x\_test, (0, 3, 1, 2))

\# Dataset to DataLoader

train\_ds = SimpleDataset(x\_train, y\_train)

test\_ds = SimpleDataset(x\_test, y\_test)

train\_loader = DataLoader(train\_ds, batch\_size)

test\_loader = DataLoader(test\_ds, batch\_size)

PyTorch Lightning trainer:

trainer = pl.Trainer(

max\_epochs = epochs,

checkpoint\_callback = False

)

Model training:

trainer.fit(self, train\_loader)

104

Chapter 2 hyperparameter OptimizatiOn

And finally, we test the trained model:

test\_loss = trainer.test(self, test\_loader)

output = self(x\_test)

predict = output.argmax(dim = 1, keepdim = True)

accuracy = round(accuracy\_score(predict, y\_test), 4)

return accuracy

Since LeNetEvolutionModel is done, we can implement the NNI trial script using

Listin[g 2-15.](#index_split_000.html#p87)

We import necessary modules and pass code root directory to system path:

***Listing 2-25.*** NNI trial script with PyTorch Lightning LeNetEvolution implementation. ch2/lenet\_to\_alexnet/pt\_trial.py

import os

import sys

import nni

\# We use relative import for user-defined modules

\# For NNI use relative import for user-defined modules

SCRIPT\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_)) + '/../..'

sys.path.append(SCRIPT\_DIR)

from ch2.lenet\_to\_alexnet.pt\_lenet\_evolution import PtLeNetEvolution

The trial method initializes the model, trains it, tests it, and returns the NNI metric: def trial(hparams):

Feature extraction hyperparameters are converted universal to form:

feat\_ext\_sequences = \[\]

for k, v in hparams.items():

if k.startswith('fe\_slot\_'):

v\['type'\] = v\['\_name'\]

feat\_ext\_sequences.append(v)

105

Chapter 2 hyperparameter OptimizatiOn

Model initialization:

model = PtLeNetEvolution(

feat\_ext\_sequences = feat\_ext\_sequences,

l1\_size = hparams\['l1\_size'\],

l2\_size = hparams\['l2\_size'\],

dropout\_rate = hparams\['dropout\_rate'\],

learning\_rate = hparams\['learning\_rate'\]

)

Next, we train the model during 50 epochs and fixed batch\_size = 16 and test it in the same method:

accuracy = model.train\_and\_test\_model(

batch\_size = 16,

epochs = 50

)

And after, we return accuracy metric to NNI tuner:

\# send final accuracy to NNI

nni.report\_final\_result(accuracy)

Next, we define the main entry point for the trial:

if \_\_name\_\_ == '\_\_main\_\_':

\# Manual HyperParameters

hparams = {

'fe\_slot\_1': {

'\_name': 'simple',

'filters': 16,

'kernel': 7

},

'fe\_slot\_2': {

'\_name': 'with\_pool',

'filters': 8,

'kernel': 5,

'pool\_size': 5

},

106

Chapter 2 hyperparameter OptimizatiOn

'fe\_slot\_3': {

'\_name': 'with\_pool',

'filters': 8,

'kernel': 5,

'pool\_size': 3

},

'l1\_size': 1024,

'l2\_size': 512,

'dropout\_rate': .3,

'learning\_rate': 0.001

}

\# NNI HyperParameters

\# Run safely without NNI Experiment Context

nni\_hparams = nni.get\_next\_parameter()

hparams.update(nni\_hparams)

trial(hparams)

Remember that a trial script can be executed in stand-alone mode, so you can run a ch2/lenet\_to\_alexnet/pt\_trial.py to test its execution with custom parameters.

**Performing LeNet Evolution HPO Experiment**

And so we come to the climax of this section. We can consider this experiment a

full- fledged scientific study that will create a unique deep learning model for a classification problem on a specific dataset. It will take the best principles of pattern recognition from the LeNet model. The LeNet Evolution model attempts to move from the LeNet model to a more complex one. Let’s define the experiment configuration and run it finally. Listin[g 2-26 con](#index_split_001.html#p120)tains the configuration for the LeNet Evolution HPO

Experiment.

***Listing 2-26.*** LeNet Evolution HPO Experiment configuration. ch2/lenet\_to\_

alexnet/config.yml

trialConcurrency: 1

107

Chapter 2 hyperparameter OptimizatiOn

We will limit the number of trials:

maxTrialNumber: 400

searchSpaceFile: search\_space.json

trialCodeDirectory: .

Uncomment PyTorch trial line to run the experiment using PyTorch implementation: trialCommand: python3 tf\_trial.py

#trialCommand: python3 pt\_trial.py

GridSearch Tuner cannot be used for search spaces that utilize nested choice, so we pick Random Search Tuner:

tuner:

name: Random

trainingService:

platform: local

The experiment can be run as follows:

nnictl create --config ch2/lenet\_to\_alexnet/config.yml

**Note** Duration ~ 18 hours on intel Core i7 with CUDa (GeForce GtX 1050)

Best trial hyperparameters returned by the experiment are listed in Table [2-6](#index_split_001.html#p122).

108

Chapter 2 hyperparameter OptimizatiOn

***Table 2-6.** LeNet Evolution best hyperparameters*

**Name**

**Values**

fe\_slot\_1

• with\_pool:

• filters: 32

• kernel: 7

• pool\_size: 5

fe\_slot\_2

• with\_pool:

• filters: 8

• kernel: 11

• pool\_size: 5

fe\_slot\_3

• simple:

• filters: 8

• kernel: 7

l1\_size

1024

l2\_size

512

dropout\_rate

0.3

learning\_rate

0.0001

The best trial demonstrated a **0.9941** accuracy on test dataset, which is an excellent result. We have indeed managed to build a model that distinguishes complex colored objects with a very high degree of accuracy. This is a good development! The reader may wonder: *Why is this section called From LeNet to AlexNet*? Well, it’s time to answer it. AlexNet is the name of a convolutional neural network architecture that won the 2012 Image Recognition competition. AlexNet classified images into 1000 different classes. At that time, it was a pretty advanced deep learning model. Let’s now compare three models: the LeNet model, the model we constructed in this section using HPO

techniques (LeNet Evolution), and the AlexNet model.

Figur[e 2-22 sho](#index_split_001.html#p123)ws that the model we built in this section for humans and horses classification is somewhere between the original LeNet model and the AlexNet model.

Our model shows a remarkable test result of **99.41%** accuracy. But most importantly, it was built entirely automatically with the help of HPO techniques and the NNI tool! We did not do any complex calculations or analytical analysis. We have just constructed a flexible LeNet Evolution model whose architecture depended on the passed

109

![](index-123_1.png)

Chapter 2 hyperparameter OptimizatiOn

hyperparameters. And as a result, we got a unique model that is fully adapted to solving a specific task. These results confirm the promise of HPO’s approach to solving deep learning problems.

***Figure 2-22.** LeNet, LeNet Evolution, AlexNet*

**Summary**

In this chapter, we started the HPO study. We studied how to create NNI experiments and solve practical problems. We managed to optimize the original LeNet model for handwritten digit recognition, upgrade the LeNet model using ReLU and dropout

techniques, and construct a new complex color pattern recognition model based on the existing LeNet model. The results that we have obtained demonstrate the promise of AutoDL. In the next chapter, we will continue to study HPO and dive into the more advanced NNI usage in Hyperparameter Optimization problems.

110

**CHAPTER 3**

**Hyperparameter**

**Optimization Under Shell**

In the previous chapter, we saw that simple HPO techniques could produce very

impressive results. Hyperparameter Optimization not only optimizes a specific model for a dataset but can even construct new architectures. But the fact is that we have used an elementary set of tools for HPO tasks so far. Indeed, up to this point, we have only used the primitive Random Search Tuner and Grid Search Tuner. We learned from the previous chapter that search spaces could contain millions and hundreds of millions of parameters. And if we had unlimited time, we could always use the Grid Search Tuner.

But unfortunately, this approach is not applicable in reality. We need Tuners that strike a good balance between speed and quality in finding the best hyperparameters. Another helpful technique is Early Stopping algorithms. Early Stopping algorithms analyze the model training process based on intermediate results and decide whether to continue training or stop it to save time.

This chapter will study various HPO Tuners and tell about their basic features. We will explore the use of Early Stopping algorithms that speed up the experiment stopping trials with an unpromising training process. And also, consider creating a custom HPO

Tuner for a particular task. This chapter will greatly enhance the practical application of the Hyperparameter Optimization approach.

**Tuners**

We begin this chapter by examining the various HPO Tuners. As you remember, Tuner receives metrics from Trial after evaluating a particular search space parameter.

Based on the existing result history of all completed Trials, Tuner decides which hyperparameter configuration to test next. The main task of the Tuner is to find the best 111

© Ivan Gridin 2022

I. Gridin, *Automated Deep Learning Using Neural Network Intelligence*,

[https://doi.org/10.1007/978-1-4842-8149-9\_3](https://doi.org/10.1007/978-1-4842-8149-9_3#DOI)

Chapter 3 hyperparameter OptimizatiOn Under Shell

hyperparameters as quickly as possible. The choice of a suitable tuner can significantly improve the result of an experiment. Let’s take a closer look at how Random Search Tuner and Grid Search Tuner act.

Consider a two-variable black-box function which is expressed in Listin[g 3-1.](#index_split_001.html#p125)

***Listing 3-1.*** Black-box function. ch3/bbf/f1.py

from ch3.bbf.utils import discrete, noise, scatter\_plot

def black\_box\_f1(x, y):

z = - 10 \* (pow(x, 5) / (3 \* pow(x \* x \* x / 4 + 1, 2) + pow(y, 4) +

10) + pow(x \* y / 2, 2) / 1000)

d = discrete(z, .8)

r = d + noise(x, y, scale = 8)

d = discrete(r, .2)

return r

I deliberately do not give an analytical formula for this function. black\_box\_f1 is just a black-box function, and we know nothing about its internal logic. In real life, black-box functions have the following properties:

• They are not continuous

• They have random noise

All black-box functions that we will examine in this chapter will satisfy these

properties. But anyway, we can cheat a little and plot this function:

if \_\_name\_\_ == '\_\_main\_\_':

scatter\_plot(black\_box\_f1, \[-10, 10\], \[-10, 10\])

Figur[e 3-1 sho](#index_split_001.html#p126)ws that the red area is where the black-box function black\_box\_f1

reaches its maximum values.

112

![](index-126_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-1.** Black-box function plot*

**Note** in this chapter, we will examine only problems of finding the maxima of the black-box function ***f***. the problem of finding the maxima of the function f is equivalent to the problem of finding the minima of the function - ***f***.

Of course, it would be great to be able to visualize a black-box function before research, but there are two main problems here:

• Most of the black-box functions have a large number of variables.

• Calculating one function value with specific parameters can take

minutes and even hours.

Therefore, of course, the choice of a Tuner has great importance. Let’s take a look at how Random Search Tuner explores the black\_box\_f1 function. We are implementing

an embedded experiment to visualize the trial parameters that the tuner has selected during the experiment in Listing [3-2](#index_split_001.html#p127).

113

Chapter 3 hyperparameter OptimizatiOn Under Shell

We import necessary modules:

***Listing 3-2.*** Random Search Tuner. ch3/tuners/random\_tuner/

run\_experiment.py

from pathlib import Path

from nni.experiment import Experiment

from ch3.bbf.f1 import black\_box\_f1

from ch3.bbf.utils import scatter\_plot

The search space for black\_box\_f1 contains all integer pairs in \[-10, 10\] × \[-10, 10\].

There are 441 elements in the search space.

search\_space = {

"x": {"\_type": "quniform", "\_value": \[-10, 10, 1\]},

"y": {"\_type": "quniform", "\_value": \[-10, 10, 1\]}

}

The experiment will have 100 trials:

experiment = Experiment('local')

experiment.config.experiment\_name = 'Random Tuner'

experiment.config.trial\_concurrency = 4

experiment.config.max\_trial\_number = 100

experiment.config.search\_space = search\_space

experiment.config.trial\_command = 'python3 trial.py'

experiment.config.trial\_code\_directory = Path(\_\_file\_\_).parent

We pick Random Search Tuner

experiment.config.tuner.name = 'Random'

and start the experiment:

http\_port = 8080

experiment.start(http\_port)

Next, we define the main event loop:

while True:

if experiment.get\_status() == 'DONE':

114

![](index-128_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

When the experiment is finished, we display all the trials that were created during the experiment:

search\_data = experiment.export\_data()

trial\_params = \[trial.parameter for trial in search\_data\]

\# Visualizing Trial Parameters

scatter\_plot(

black\_box\_f1, \[-10, 10\], \[-10, 10\],

trial\_params, title = 'Random Search'

)

search\_metrics = experiment.get\_job\_metrics()

input("Experiment is finished. Press any key to exit...")

break

Let’s examine all the trials that Random Search Tuner generated during the

experiment in Listing [3-2.](#index_split_001.html#p127)

Figur[e 3-2 sho](#index_split_001.html#p128)ws that the trials generated by Random Search Tuner are simple random dots scattering. In some cases, the dot (trial) may successfully fall into the area of maximum values, but in many cases, the area of maximum values remains unexplored properly.

***Figure 3-2.** Random Search Tuner Trials*

115

![](index-129_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

Let’s now look at the trials that the Grid Search Tuner generates by exploring the black\_box\_f1 function in Listin[g 3-3.](#index_split_001.html#p129)

***Listing 3-3.*** Grid Search Tuner. ch3/tuners/grid\_tuner/run\_experiment.py experiment.config.tuner.name = 'GridSearch'

The Grid Search experiment looks much like the Random Search experiment in

Listin[g 3-2. W](#index_split_001.html#p127)e only use Grid Search Tuner here:

Figur[e 3-3 demons](#index_split_001.html#p129)trates the trials generated by the Grid Search Tuner.

***Figure 3-3.** Grid Search Tuner Trials*

We see that the Grid Search Tuner simply iterates through all the values in the search space in a particular order. This approach can be helpful when dealing with a small search space when it is possible to iterate over all the values in the search space.

Otherwise, the trials generated by Grid Search Tuner may not even get close to the area of maximum values of the black-box function.

116

![](index-130_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

The main problem with Random and Grid tuners is that they don’t interact with

their trial results in any way. They do not have any “memory” that would allow them to highlight promising areas in the search space and concentrate their search on them. We will now begin to study tuners that have “memory” and which can explore the search space more efficiently.

**Evolution Tuner**

Evolution Tuner search is based on the principles of natural evolution. It implements two fundamental principles of evolution: selection and mutation. Evolution Tuner initializes a population of a specific size. Each population individual represents a particular set of parameters in the search space. Each individual has a fitness property that indicates the Trial result. We say that individual A is better than individual B:

• If A.fitness > B.fitness when the Tuner runs in

maximization mode

• If A.fitness < B.fitness when the Tuner runs in

minimization mode

Evolution Tuner takes the best individual from a random pair of individuals and

mutates it randomly by replacing the value of its parameter with another value from the search space. After that, the mutated individual replaces the original one, and the process is repeated again. Figur[e 3-4 illus](#index_split_001.html#p130)trates this search principle.

***Figure 3-4.** Evolution Tuner*

117

Chapter 3 hyperparameter OptimizatiOn Under Shell

One of the big problems with Evolution Tuner is that mutation doesn’t always

improve an individual’s fitness. Mutation operation only executes a random change in parameter values, and usually, mutation degrades an individual’s performance.

**Note** the experienced reader may notice that evolutionary algorithms based on the principles of natural selection have another key method – *crossover*. But many studies show that most evolutionary problems can be solved without the *crossover* operation. this implementation of evolution tuner does not contain *crossover* operation.

Here is an example of Evolution Tuner configuration:

\# config.yml

tuner:

name: Evolution

classArgs:

optimize\_mode: maximize

population\_size: 100

Evolution Tuner supports all search space types: choice, choice(nested), randint, uniform, quniform, loguniform, qloguniform, normal, qnormal, lognormal, and

qlognormal.

Let’s take a look at Evolution Tuner in action optimizing black\_box\_f1 function in Listin[g 3-4.](#index_split_001.html#p131)

(Full code is provided in the corresponding file: *ch3/tuners/evolution\_tuner/*

*run\_experiment.py*.)

Setting population size:

***Listing 3-4.*** Evolution Tuner

population\_size = 8

Picking the Evolution Tuner for the Experiment:

experiment.config.tuner.name = 'Evolution'

experiment.config.tuner.class\_args\['optimize\_mode'\] = 'maximize'

experiment.config.tuner.class\_args\['population\_size'\] = population\_size

118

Chapter 3 hyperparameter OptimizatiOn Under Shell

Unlike Grid Search Tuner and Random Search Tuner, an Evolution Tuner has

“memory.” That is why it is more attractive to analyze the search process progress.

We will show the history of the allocation of trial parameters in the search space by generations:

• **1st generation**: From 1st trial to 25th trial

• **2nd generation**: From 26th trial to 50th trial

• **3rd generation**: From 51st trial to 75th trial

• **4th generation**: From 76th trial to 100th trial

This approach will allow us to observe the search progress in action:

\# Event Loop

while True:

if experiment.get\_status() == 'DONE':

search\_data = experiment.export\_data()

The history of trials:

trial\_params = \[trial.parameter for trial in search\_data\]

Splitting trial history by generations:

trial\_params\_chunks = \[

trial\_params\[i:i + 25\]

for i in range(0, len(trial\_params), 25)

\]

Visualizing each generation:

for i, population in dict(enumerate(trial\_params\_chunks)).items():

scatter\_plot(

black\_box\_f1, \[-10, 10\], \[-10, 10\],

population, title = f'Evolution Generation: {i+1}'

)

Let’s analyze how the position of individuals changed during the

evolutionary search.

119

![](index-133_1.png)

![](index-133_2.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-5.** Evolution Tuner. Generation: 1*

Figur[e 3-5](#index_split_001.html#p133) shows that the allocation of trial parameters is close to random distribution.

***Figure 3-6.** Evolution Tuner. Generation: 2*

120

![](index-134_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

In Figur[e 3-6, w](#index_split_001.html#p133)e see that most of the individuals are already in the red zone, which means that the population is moving smoothly toward the highest values of the function.

And the last generation shown in Figur[e 3-7 h](#index_split_001.html#p134)as at least one individual at the top of the red zone.

***Figure 3-7.** Evolution Tuner. Generation: 4*

**Note** not all built-in nni tuners support random seed setting. hence, the experiments are not reproducible. therefore, the results you get on your local

machine may differ from those shown in this chapter. however, the general

behavior of tuners remains the same on all machines, so the results of the same

tuner on the same search space are similar.

We can consider the Evolution Tuner as a directed random search. It is slightly better than random search but still has many problems due to the too random nature of this algorithm. Evolution Tuner usually requires many trials but is usually selected due to its simplicity.

121

Chapter 3 hyperparameter OptimizatiOn Under Shell

**Anneal Tuner**

Anneal Tuner is based on the Simulated Annealing algorithm. Simulated Annealing is a method for solving optimization problems. The algorithm models the physical process of heating a material and slowly lowering the temperature to decrease defects, thus minimizing the system energy. Annealing Tuner uses randomness as part of the search process like Evolution Tuner.

The annealing algorithm consists of the following steps:

1\. The annealing algorithm selects a random element X in the

search space, and the f(X) value is calculated.

2\. The algorithm performs a random mutation on element X

producing X’ element from the search space.

If X is a real value, then X’ can be calculated as X’ = X + ΔX, where

ΔX is a random variable. Next, we compare f(X’) and f(X).

3a. If f(X’) < f(X), then the mutation is considered as negative.

3b. If f(X’) ≥ f(X), then the mutation is considered as positive

and X value is updated by X’.

4\. If the mutation is negative, then the algorithm calculates the

following values:

• *r*: Uniform random value on (0, 1).

• Δ: f(X) - f(X’).

• *σ* is standard deviation of all explored values during the

search: f(X1), ..., f(Xn) multiplied by degradation ratio *ci*, where

*c* is the positive value lower than 1 and *i* is the number of

iteration, σ = *ci* *std*(\[f(X1), …, f(Xn)\]).

Next, we compare *r* and *e* , where *e* is the exponential.

5a. If *r* < *e* , then the algorithm degrades from X to X’: X ← X’.

This is done hoping that it will be possible to reach a new

peak in the next iteration and the transition to X’ is only an

intermediate step. We can consider this as an exploration

step that explores an area near X in the search space.

122

![](index-136_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

5b. If

*r* > *e* , then the algorithm doesn’t update X.

The closer f(X) is to f(X’), the more likely an exploration step would be taken.

Steps from 2 to 5 are repeated *n* times. Figur[e 3-8 demons](#index_split_001.html#p136)trates the annealing algorithm flow.

***Figure 3-8.** Annealing algorithm flow*

The essence of the annealing algorithm is to get to the “hills” of the surface of the black-box function *f* and study the area of this “hill.” In some cases, the algorithm may descend from “hills” hoping to climb to a higher one. The disadvantage of this algorithm is that it cannot cover large distances between different “hills” of the surface of the function f. Figur[e 3-9 demons](#index_split_001.html#p137)trates the annealing algorithm in action.

123

![](index-137_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-9.** Annealing algorithm in action*

Here is an example of Anneal Tuner configuration:

\# config.yml

tuner:

name: Anneal

classArgs:

population\_size: 100

Anneal Tuner supports all search space types: choice, choice(nested), randint,

uniform, quniform, loguniform, qloguniform, normal, qnormal, lognormal, and

qlognormal.

Listin[g 3-5 illus](#index_split_001.html#p137)trates another black-box function holder\_function, based on Holder’s function. We will use it for testing Anneal Tuner performance.

***Listing 3-5.*** Holder’s black-box function. ch3/bbf/holder.py

from numpy import exp, sqrt, cos, sin, pi

def holder\_function(x, y):

"""

Holder's function

"""

z = abs(sin(x) \* cos(y) \* exp(abs(1 - (sqrt(x\*\*2 + y\*\*2) / pi))))

124

![](index-138_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

d = discrete(z, .8)

r = d + noise(x, y, scale = 8)

d = discrete(r, .2)

return r

holder\_function can be plotted the following way:

from ch3.bbf.utils import scatter\_plot, discrete, noise

if \_\_name\_\_ == '\_\_main\_\_':

scatter\_plot(holder\_function, \[-10, 10\], \[-10, 10\])

Figur[e 3-10 sho](#index_split_001.html#p138)ws the surface of holder\_function function. This surface is much more challenging to explore. It has many hills that are evenly spaced on the surface. The highest peaks are in the left corners.

***Figure 3-10.** Holder’s function*

Let’s examine how Anneal Tuner performs optimizing holder\_function in

Listin[g 3-6.](#index_split_001.html#p139)

(Full code is provided in the corresponding file: *ch3/tuners/anneal\_tuner/*

*run\_experiment.py*.)

125

![](index-139_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

Picking the Anneal Tuner for the Experiment:

***Listing 3-6.*** Anneal Tuner

experiment.config.tuner.name = 'Anneal'

experiment.config.tuner.class\_args\['optimize\_mode'\] = 'maximize'

After the experiment is completed, we can analyze the progress of the search for Anneal Tuner.

***Figure 3-11.** Anneal Tuner. Generation: 1*

In Figur[e 3-11](#index_split_001.html#p139), we can see that Anneal Tuner is starting to study the “hills” in the lower-left corner.

126

![](index-140_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-12.** Anneal Tuner. Generation: 2*

Figur[e 3-12 demons](#index_split_001.html#p140)trates that the second generation of trials is completely focused on the two “hills” in the lower-left corner.

And as we can see in Figure [3-13](#index_split_001.html#p141), Anneal Tuner is completely concentrated on exploring only one “hill.” Anneal Tuner found a local maxima but could not find global maxima at the bottom of the left corner, close to the solution Anneal Tuner found.

127

![](index-141_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-13.** Anneal Tuner. Generation: 4*

Anneal Tuner and Evolution Tuner are variants of directed random search. They

are intuitive and straightforward, but they may not always explore the search space effectively. Let’s study more advanced tuners based on the Bayesian optimization approach.

**Sequential Model-Based Optimization Tuners**

In this section, we will examine tuners that are based on Sequential Model-Based Optimization (SMBO). SMBO is a formulation of the Bayesian Optimization approach.

SMBO implements the following technique: building a probability model p(y|x) of the black-box function *f* and use it to pick the most promising elements in the search space to evaluate in the black-box function *f*.

Examine the SMBO method in action. Say we have some trial results we obtained:

(x1, f(x1)), (x2, f(x2), (x3, f(x3)), as is shown in Figur[e 3-14.](#index_split_001.html#p142)

128

![](index-142_1.png)

![](index-142_2.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-14.** Trial results*

The next step is to create a probability function p(y|x) based on the data: (x1, f(x1)), (x2, f(x2), (x3, f(x3)). p(y|x) is called a “surrogate” for the objective (or black-box) function.

The surrogate function determines the probability distribution of the objective (or black-box) function for any element xi in the search space. This means that for any x *i*, we can say that with a *p* probability, the value f(x *i*) = y *i* lies in the (a, b) interval. This concept is demonstrated in Figure [3-15.](#index_split_001.html#p142)

***Figure 3-15.** Probability distributions for xi and xj*

129

![](index-143_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

Having surrogate function p(x|y), we can extrapolate it on the whole search space.

Figur[e 3-16 giv](#index_split_001.html#p143)es a visual description of the surrogate model:

• Red dashed line shows the actual black-box function.

• Black solid line shows the expected mean of the surrogate

function p(y|x).

• Purple dashed line shows the variance of the surrogate

function p(y|x).

***Figure 3-16.** Surrogate model for three trials: (x1, f(x1)), (x2, f(x2)), (x3, f(x3))* Based on the constructed surrogate model, the SMBO algorithm makes its prediction regarding the potential maxima of the black-box function. The next goal of the algorithm is to find a higher value of the black-box function than the current maximum value f(x2). The following trial parameters are determined using the Expected Improvement function:

EI

max *y*

*y*,0 *p* *y*| *x* *dy*

y\*(x) =

If we assume that f(x *2*) = y2, then SMBO will choose x4 as the next trial parameter if the EIy2(x) will be maximum with x4. Figure [3-17 illus](#index_split_001.html#p144)trates the next trial selection by SMBO algorithm.

130

![](index-144_1.png)

![](index-144_2.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-17.** Expected Improvement*

After selecting the x *4* as the next trial value, we evaluate f(x *4*) and rebuild the surrogate model concerning the new data: *(x1, f(x1)), (x2, f(x2)), (x3, f(x3)), (x4, f(x4))* as shown in Figure [3-18.](#index_split_001.html#p144)

***Figure 3-18.** Surrogate model for four trials: (x1, f(x1)), (x2, f(x2)), (x3, f(x3)),* *(x4, f(x4))*

131

Chapter 3 hyperparameter OptimizatiOn Under Shell

SMBO aims to converge the surrogate model to the objective function with more

data, which these approaches do by continually updating the surrogate probability model after each objective function evaluation. SMBO Tuners are efficient because they choose the next parameters in an informed way.

SMBO Tuner performs the following steps in a cycle until the maximum number of

trials is reached:

• Construct surrogate model based on surrogate probability p(y|x).

• Determine next trial parameter x using the Estimated Improvement

function.

• Evaluate black-box function f(x).

• Append *(x, f(x))* pair to historical dataset.

This is the framework for all SMBO Tuners. The only difference between them is

the p(y|x) function definition. Different SMBO Tuners have different approaches to estimating the probability function p(y|x) based on a historical dataset. This chapter will cover the following SMBO Tuners: Tree-Structured Parzen Estimator Tuner and Gaussian Process Tuner.

**Tree-Structured Parzen Estimator Tuner**

The Tree-Structured Parzen Estimator Tuner (TPE) description may take one or several separate chapters. In this section, we will describe the main idea behind the use of this Tuner:

1\. In the beginning, TPE Tuner performs *N* random trials while

exploring the search space.

2\. Next, the Tuner sorts the executed trials by their values and

divides them into “good” and “bad” groups based on some

quantile - γ. The first group, “good” group, contains trials that gave

the best results and the “bad” one, all other trials.

Figur[e 3-19 depicts the TP](#index_split_001.html#p146)E model after the first two steps.

132

![](index-146_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-19.** TPE Tuner. “Good” and “bad” separation*

3\. Densities

*l*(x) and *g*(x) are calculated using Parzen Estimators

(also known as kernel density estimators) for “bad” and “good”

groups, respectively. Parzen Estimators are a simple average of

kernels centered on existing data points.

4\. After, the TPE tuner generates *n* random candidates according

to the *g*(x) density function. Each of these candidates is sorted

by *g*(x)/ *l*(x) ratio, and the first one is picked as the next trial.

This means that the TPE tuner allows the selection of random

candidates in an area where “good” trials are more common. At

the same time, all candidates are sorted according to *g*(x)/ *l*(x), which means that a candidate with a high density of good trials

and a low density of bad trials will be selected. This approach

strikes a good balance between exploration and exploitation.

Figur[e 3-20 illus](#index_split_001.html#p147)trates the algorithm of selecting the next trial parameter.

133

![](index-147_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-20.** TPE Tuner. Next candidate selection*

5\. Repeat steps 2–5 until maximum number of trials is reached.

Here is an example of TPE Tuner configuration:

\# config.yml

tuner:

name: TPE

classArgs:

optimize\_mode: maximize

seed: 12345

tpe\_args:

constant\_liar\_type: 'mean'

n\_startup\_jobs: 10

n\_ei\_candidates: 20

linear\_forgetting: 100

prior\_weight: 0

gamma: 0.5

The following is the description of TPE Tuner parameters:

• tpe\_args.constant\_liar\_type:

**Type**: 'best' | 'worst' | 'mean' | null

**Default**: 'best'

134

Chapter 3 hyperparameter OptimizatiOn Under Shell

TPE algorithm itself does not support parallel tuning. This

parameter specifies how to optimize for trial\_concurrency > 1.

In general, best suit for small trial number and worst suit for large

trial number.

• tpe\_args.n\_startup\_jobs:

**Type**: int

**Default**: 20

The first *N* random trials are generated for warming up in Step 1. If

the search space is large, this value should be increased.

• tpe\_args.n\_ei\_candidates:

**Type**: int

**Default**: 24

*n* random candidates generated in Step 4.

• tpe\_args.linear\_forgetting:

**Type**: int

**Default**: 25

TPE lowers the weights of old trials. This parameter controls how

many iterations it takes for a trial to start decay.

• tpe\_args.prior\_weight:

**Type**: float

**Default**: 1.0

Determines the weight of trial configuration in the history trial

configurations.

• tpe\_args.gamma:

**Type**: float

**Default**: 0.25

Controls how many trials are considered “good.” Represents γ

parameter from Step 2.

135

Chapter 3 hyperparameter OptimizatiOn Under Shell

**Note** tpe tuner configuration parameters mentioned above are only valid from nni version 2.6. they will not work on previous versions.

TPE Tuner supports all search space types: choice, choice(nested), randint,

uniform, quniform, loguniform, qloguniform, normal, qnormal, lognormal, and

qlognormal.

We can see from Listin[g 3-7 ho](#index_split_001.html#p149)w TPE Tuner performs optimizing holder\_function.

(Full code is provided in the corresponding file: *ch3/tuners/tpe\_tuner/*

*run\_experiment.py*.)

Setting the TPE Tuner for the Experiment:

***Listing 3-7.*** TPE Tuner

experiment.config.tuner.name = 'TPE'

experiment.config.tuner.class\_args\['optimize\_mode'\] = 'maximize'

experiment.config.tuner.class\_args\['seed'\] = 0

experiment.config.tuner.class\_args\['tpe\_args'\] = {

'n\_startup\_jobs': 20,

'gamma': 0.5

}

After the experiment is completed, we can analyze the progress of the search for TPE Tuner.

136

![](index-150_1.png)

![](index-150_2.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-21.** TPE Tuner. Generation: 1*

Figur[e 3-21 sho](#index_split_001.html#p150)ws that the distribution of points is more like a random scattering, which makes sense because, in the tuner setup, we specified 'n\_startup\_jobs': 20, which means that the first 20 trials will be completely random.

***Figure 3-22.** TPE Tuner. Last generation*

137

Chapter 3 hyperparameter OptimizatiOn Under Shell

But as we see in Figure [3-22, the TP](#index_split_001.html#p150)E Tuner finds the global maxima of holder\_function, thanks to a probabilistic exploration model.

The TPE Tuner is intuitively clear, based on a solid probability ground, and has a good balance between exploration and exploitation policy. Another nice feature is that it supports choice(nested) search type, which can be critical in some research.

**Gaussian Process Tuner**

Gaussian Process (GP) Tuner is another SMBO Tuner based on Multivariate Normal

Distribution. This tuner is similar to the TPE Tuner but uses a Gaussian distribution to build the p(y|x) surrogate. A full description of this method lies outside of this book, but the reader can learn how this method works here:

• “Using Gaussian Processes to Optimize Expensive Functions”:

[https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.139.9315&rep=rep1&type=pdf)

[1.139.9315&rep=rep1&type=pdf](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.139.9315&rep=rep1&type=pdf)

• “Gaussian Processes and Bayesian Optimiza[tion”: www.cs.cornell.](http://www.cs.cornell.edu/courses/cs4787/2019sp/notes/lecture16.pdf)

[edu/courses/cs4787/2019sp/notes/lecture16.pdf](http://www.cs.cornell.edu/courses/cs4787/2019sp/notes/lecture16.pdf)

Here is an example of GP Tuner configuration:

\# config.yml

tuner:

name: GPTuner

classArgs:

optimize\_mode: maximize

utility: 'ei'

kappa: 5.0

xi: 0.0

nu: 2.5

alpha: 1e-6

cold\_start\_num: 10

selection\_num\_warm\_up: 100000

selection\_num\_starting\_points: 250

138

Chapter 3 hyperparameter OptimizatiOn Under Shell

The following is the description of GP Tuner parameters:

• utility:

**Type**: 'ei' | 'ucb' | 'poi'

**Default**: 'ei'

The utility functions ei, ucb, and poi correspond to Expected

Improvement, Upper Confidence Bound, and Probability of

Improvement, respectively.

• kappa:

**Type**: float

**Default**: 5

Used by the ucb utility function. The bigger the kappa is, the more

exploratory the tuner will be.

• xi:

**Type**: float

**Default**: 0

Used by the ei and poi utility functions. The bigger the xi is, the

more exploratory the tuner will be.

• nu:

**Type**: float

**Default**: 2.5

Sets the Matern kernel. The smaller the nu is, the less smooth the

approximated function will be.

• alpha:

**Type**: float

**Default**: 1e-6

Sets the Gaussian Process Regressor. Larger values correspond to

an increased noise level in the observations.

139

Chapter 3 hyperparameter OptimizatiOn Under Shell

• cold\_start\_num:

**Type**: int

**Default**: 10

Number of random explorations to perform before the Gaussian

Process.

• selection\_num\_warm\_up:

**Type**: int

**Default**: 1e5

Number of random points to evaluate when getting the point

which maximizes the acquisition function.

• selection\_num\_starting\_points:

**Type**: int

**Default**: 250

Number of times to run L-BFGS-B from a random starting point

after the warm-up.

GP Tuner supports the following search space types: choice, randint, uniform,

quniform, loguniform, and qloguniform.

GP Tuner suffers a lot from parallelization issues. If you run an experiment in

concurrency mode (i.e., trial\_concurrency > 1), multiple processes simultaneously decide on their next trial candidate based on the same historical data. Therefore, different processes are testing the same parameters at the same time. This is a big problem with all SMBO tuners. But TPE Tuner can get around this problem with the Constant Liar technique, while for GP Tuner, this problem remains serious. In Figur[e 3-23, w](#index_split_001.html#p154)e can see the Trial Metric panel for GP Tuner with trial\_concurrency = 8. It shows that GP Tuner contains chunks of the same trials, which does not speed up the process of exploring the search space in any way.

140

![](index-154_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-23.** GP Tuner. Concurrency issue*

Listin[g 3-8 im](#index_split_001.html#p154)plements GP Tuner for holder\_function optimization task.

(Full code is provided in the corresponding file: *ch3/tuners/gp\_tuner/run\_*

*experiment.py*.)

Disabling concurrency:

***Listing 3-8.*** GP Tuner

experiment.config.trial\_concurrency = 1

Setting the GP Tuner for the Experiment:

experiment.config.tuner.name = 'GPTuner'

experiment.config.tuner.class\_args\['optimize\_mode'\] = 'maximize'

GP Tuner shows excellent results. Figure [3-24](#index_split_001.html#p155) shows the coordinates of all trials during the experiment. GP Tuner found both global maxima and evenly explored the entire search space.

141

![](index-155_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-24.** GP Tuner. Holder’s black-box function optimization*

GP Tuner suggests taking search space elements to find a suitable solution in a small number of black-box function evaluations. GP Tuner carries about the surrogate model instead of the black-box function itself, using the conjugate gradient method to find the highest expected improvement candidates. GP Tuner shows good exploratory behavior in testing out areas that seem promising under the current surrogate model.

**Which Tuner to Choose?**

In this section, we’ve put a lot of effort into learning about the different tuners, and the fair question might be: *Hey, so which tuner should I choose?* And the answer to this question is disappointing: according to the **No Free Lunch Theorem**, which we already considered in Chapter [1,](https://doi.org/10.1007/978-1-4842-8149-9_1) ***there is no search algorithm (Tuner) that would have any***

***advantages over other Tuners for an arbitrary search space***. Indeed, for an arbitrary search space, the expectation of the TPE Tuner does not exceed the Random Tuner

expectation. So why do we need any Tuners at all if all of them are equal to Random Tuner on an arbitrary search space?!

142

Chapter 3 hyperparameter OptimizatiOn Under Shell

And the answer is as follows: search spaces have a specific structure and

dependencies that allow certain Tuners to outperform others for many kinds of

problems. Therefore, if we know that we are optimizing a model for an image

classification problem, this can give us some insight into the search space structure.

Consequently, we can choose a Tuner that is more likely to show good results

than others.

There is a separate area of research in which scientists arrange battles of search algorithms to determine the best one for a particular class of problems. Scientists use benchmarks to estimate the characteristics of the search algorithm. The benchmark algorithm evaluates the search algorithm several times for different search spaces. For example, the benchmark pseudo-code might look like this:

\# search\_algos: List of competing Search Algorithms

\# problems: List of similar problems

\# results: Map (Dict) of results

for algo in search\_algos:

for p in problems:

metrics = algo(p)

results\[algo\].append(metrics)

\# Sort algorithms by results

In Table [3-1, I pr](#index_split_001.html#p156)ovide a sample benchmark result obtained using NNI

[https://nni.readthedocs.io/en/v2.7/hpo/hpo\_benchmark\_stats.html.](https://nni.readthedocs.io/en/v2.7/hpo/hpo_benchmark_stats.html)

***Table 3-1.** Average rankings for classification tasks*

**Tuner Name**

**Average Ranking**

Gp tuner

4.00

evolution

4.22

anneal

4.39

tpe

4.67

random

5.33

143

Chapter 3 hyperparameter OptimizatiOn Under Shell

Some benchmarks can last several days or even weeks. Therefore, it is always more convenient to borrow the results obtained and published after research. In many cases, you can execute a mini-research yourself, which will help determine the characteristics of the search space structure. In any case, understanding the deep learning model optimization problem and principles of the Search Tuner is very helpful in choosing the right strategy for solving the HPO problem.

**Custom Tuner**

Built-in tuners are suitable for most tasks. But there are situations when you need to add some custom logic to improve the quality of the HPO Experiment. Indeed, sometimes, we may know specific properties of the search space that the built-in tuner does not take into account. Also, the developer can implement their original idea and test it on real problems. For such cases, NNI allows you to implement a Custom Tuner. Custom Tuner can be used in an experiment and shared with other developers.

**Tuner Internals**

Each Tuner class should inherit nni.tuner.Tuner and implement the following

methods: \_\_init\_\_, update\_search\_space, generate\_parameters, receive\_trial\_

result. Any Tuner can be implemented based on the self-describing sample presented in Listing [3-9](#index_split_001.html#p157).

***Listing 3-9.*** Custom Tuner. ch3/tuners/custom\_tuner/custom\_tuner\_sample.py from nni.tuner import Tuner

**class CustomTunerSample(Tuner):**

**def \_\_init\_\_(self, some\_arg) -> None:**

\# YOUR CODE HERE #

...

**def update\_search\_space(self, search\_space):**

"""

Tuners are advised to support updating search

space at run-time. If a tuner can only set

144

Chapter 3 hyperparameter OptimizatiOn Under Shell

search space once before generating first

hyper-parameters, it should explicitly document

this behaviour. 'update\_search\_space' is called

at the startup and when the search space is updated.

"""

\# YOUR CODE HERE #

...

**def generate\_parameters(self, parameter\_id, \*\*kwargs):**

"""

This method will get called when the framework

is about to launch a new trial. Each parameter\_id

should be linked to hyper-parameters returned by

the Tuner. Returns hyper-parameters, a dict

in most cases.

"""

\# YOUR CODE HERE #

\# Example: return {"dropout": 0.5, "act": "relu"}

return {}

**def receive\_trial\_result(self, parameter\_id, parameters, value,**

**\*\*kwargs):**

"""

This method is invoked when a trial reports

its final result. Should be implemented

if Tuner assumes 'memory', i.e.,

Tuner is tracking previous Trials

"""

\# YOUR CODE HERE #

Tuner interacts with Experiment the following way:

1\. Experiment calls update\_search\_space at the startup.

2\. Experiment requests search space parameters for Trial calling

generate\_parameters.

145

![](index-159_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

3\. Experiment returns Trial results to Tuner calling

recieve\_trial\_result.

(Steps 2 and 3 are repeated until max\_trial\_number is reached or Experiment is

stopped.)

Figur[e 3-25 sho](#index_split_001.html#p159)ws Tuner–Experiment interaction as a sequence diagram.

***Figure 3-25.** Tuner–Experiment sequence diagram*

146

Chapter 3 hyperparameter OptimizatiOn Under Shell

Custom Tuner is integrated into the experiment using the following config:

tuner:

codeDirectory: <path\_to\_tuner\_dir>

className: <tuner\_file\_name>.<class\_name>

Or it can be integrated into Python embedded experiment as follows:

from nni.experiment import CustomAlgorithmConfig

experiment.config.tuner = CustomAlgorithmConfig()

experiment.config.tuner.code\_directory = 'path\_to\_tuner\_dir'

experiment.config.tuner.class\_name = 'tuner\_file\_name.class\_name'

experiment.config.tuner.class\_args = {'arg': 'value'}

**New Evolution Custom Tuner**

Let’s try to develop our Сustom Tuner. This Tuner will be based on the evolutionary concepts we examined exploring the Evolution Tuner. We’ll call it NewEvolutionTuner.

NewEvolutionTuner will initialize the population and act according to the following algorithm:

• Take the best individual: Xbest

• Mutate the best individual in a random way: *mutate*(Xbest) → Y

• Replace the worst individual in the population Xworst with a mutant of

the best individual Y: Xworst ← Y

Figur[e 3-26 demons](#index_split_001.html#p161)trates the search approach of NewEvolutionTuner: 147

![](index-161_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-26.** New Evolution Tuner*

NewEvolutionTuner implements a greedy “hill-climbing” approach. The Tuner takes

the best individual (the highest one) and mutates it (hoping that the new individual will climb higher). Listing [3-10 us](#index_split_001.html#p161)e NewEvolutionTuner to find the maxima of Ackley’s function.

***Listing 3-10.*** Ackley’s function. ch3/bbf/ackley.py

from numpy import exp, sqrt, cos, pi, e

from ch3.bbf.utils import noise

def ackley\_function(x, y):

"""

Ackley’s function

"""

z = 20.0 \* exp(-0.2 \* sqrt(0.5 \* (x\*\*2 + y\*\*2))) -\\

exp(0.5 \* (cos(2 \* pi \* x) + cos(2 \* pi \* y))) + e + 20

r = z + noise(x, y, scale = 4)

return r

And here is Ackley’s function visualization:

from ch3.bbf.utils import scatter\_plot

if \_\_name\_\_ == '\_\_main\_\_':

scatter\_plot(ackley\_function, \[-10, 10\], \[-10, 10\])

148

![](index-162_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

We can see in Figure [3-27](#index_split_001.html#p162) the surface of Ackley’s function. It has one highest hill and several smaller hills nearby.

***Figure 3-27.** Ackley’s function*

Before we check how NewEvolutionTuner solves the problem of finding the maxima

of Ackley’s function, we need to implement it in Listing [3-11](#index_split_001.html#p162).

Importing necessary modules:

***Listing 3-11.*** NewEvolutionTuner. ch3/tuners/custom\_tuner/evolution\_tuner.py import random

import numpy as np

from nni.tuner import Tuner

from nni.utils import (

OptimizeMode, extract\_scalar\_reward,

json2space, json2parameter,

)

149

Chapter 3 hyperparameter OptimizatiOn Under Shell

Population consists of individuals. Each individual has DNA that represents a

search space parameter. Also, individual has a result field that contains Trial result. New Evolution individual has the following properties:

• x: Search space *x* coordinate

• y: Search space *y* coordinate

• param\_id: Trial number

• result: Trial result

class **Individual:**

def **\_\_init\_\_(**self, x, y, param\_id = None) -> None:

self.param\_id = param\_id

self.x = x

self.y = y

self.result = None

def **to\_dict**(self):

return {'x': self.x, 'y': self.y}

Population class is a wrapper that manipulates all individuals as a whole:

class **Population**:

All individuals are stored in individuals property:

def **\_\_init\_\_**(self) -> None:

self.individuals = \[\]

def **add**(self, ind):

self.individuals.append(ind)

Then, we need to add a method that will return an individual by its param\_id:

def **get\_by\_param\_id**(self, param\_id):

for ind in self.individuals:

if ind.param\_id == param\_id:

return ind

return None

150

Chapter 3 hyperparameter OptimizatiOn Under Shell

At the start of the experiment, the Tuner will create *N* individuals who will not have a trial number. We will call these individuals virgins. get\_first\_virgin method returns the first virgin found in population:

def **get\_first\_virgin**(self):

for ind in self.individuals:

if ind.param\_id is None:

return ind

return None

The following method – get\_population\_with\_result – returns all individuals that already received a trial result:

def **get\_population\_with\_result**(self):

population\_with\_result = \[ind for ind in self.individuals if

ind.result is not None\]

return population\_with\_result

The next method returns the best individual from the whole population, that is, an individual that has the highest result:

def **get\_best\_individual**(self):

sorted\_population = sorted(self.get\_population\_with\_result(),

key = lambda ind: ind.result)

return sorted\_population\[-1\]

And here, we come to our primary evolution method replace\_worst, which will

develop the population:

• We take the best individual from the population.

• Mutate the best individual.

• Add the mutant of the best individual to the population instead of the

worst one.

def **replace\_worst**(self, param\_id):

population\_with\_result = self.get\_population\_with\_result()

sorted\_population = sorted(population\_with\_result, key = lambda

ind: ind.result)

worst = sorted\_population\[0\]

151

Chapter 3 hyperparameter OptimizatiOn Under Shell

self.individuals.remove(worst)

best = self.get\_best\_individual()

x = round(best.x + random.gauss(0, 1), 2)

y = round(best.y + random.gauss(0, 1), 2)

mutant = Individual(x, y, param\_id)

self.individuals.append(mutant)

return mutant

We can start implementing the tuner after defining the Individual and Population classes:

class **NewEvolutionTuner**(Tuner):

The Tuner has two parameters, optimize\_mode and population size:

def **\_\_init\_\_**(self, optimize\_mode = "maximize", population\_size = 16)

\-> None:

self.optimize\_mode = OptimizeMode(optimize\_mode)

self.population\_size = population\_size

Next, Tuner initializes properties related to the search space it is working with: self.search\_space\_json = None

self.random\_state = None

self.population = Population()

self.space = None

When the Tuner starts, the update\_search\_space method is invoked. It generates the Population of Random Individuals:

def **update\_search\_space**(self, search\_space):

self.search\_space\_json = search\_space

self.space = json2space(self.search\_space\_json)

self.random\_state = np.random.RandomState()

\# Population of Random Individuals is generated

is\_rand = dict()

for item in self.space:

is\_rand\[item\] = True

152

Chapter 3 hyperparameter OptimizatiOn Under Shell

for \_ in range(self.population\_size):

params = json2parameter(self.search\_space\_json, is\_rand, self.

random\_state)

ind = Individual(params\['x'\], params\['y'\])

self.population.add(ind)

Experiment calls generate\_parameters method to get new parameters for the

subsequent Trial. Initially, we have a set of individuals generated at the startup and not passed to the Tuner (virgins). We take virgins and pass them to Tuner one by one. When no virgins are left, we are generating new individuals.

def **generate\_parameters**(self, parameter\_id, \*\*kwargs):

virgin = self.population.get\_first\_virgin()

if virgin:

virgin.param\_id = parameter\_id

return virgin.to\_dict()

else:

mutant = self.population.replace\_worst(parameter\_id)

return mutant.to\_dict()

When the Experiment returns the Trial’s result, we save it to an individual object: def **receive\_trial\_result**(self, parameter\_id, parameters, value,

\*\*kwargs):

reward = extract\_scalar\_reward(value)

ind = self.population.get\_by\_param\_id(parameter\_id)

ind.result = reward

Well, our NewEvolutionTuner is ready for action! We can launch the experiment

using the following config file shown in Listing [3-12.](#index_split_001.html#p166)

***Listing 3-12.*** NewEvolutionTuner Experiment configuration. ch3/tuners/

custom\_tuner/config.yml

searchSpace:

x:

\_type: "quniform"

\_value: \[-10, 10, 0.01\]

153

Chapter 3 hyperparameter OptimizatiOn Under Shell

y:

\_type: "quniform"

\_value: \[-10, 10, 0.01\]

trialConcurrency: 4

trialCodeDirectory: .

trialCommand: python3 trial.py

tuner:

codeDirectory: .

className: evolution\_tuner.NewEvolutionTuner

trainingService:

platform: local

The experiment with custom NewEvolutionTuner can also be run in Python

embedded mode as it is implemented in Listin[g 3-13.](#index_split_001.html#p167)

(Full code is provided in the corresponding file: *ch3/tuners/custom\_tuner/*

*run\_experiment.py*.)

***Listing 3-13.*** Python embedded experiment

experiment.config.tuner = CustomAlgorithmConfig()

experiment.config.tuner.code\_directory = Path(\_\_file\_\_).parent

experiment.config.tuner.class\_name = 'evolution\_tuner.NewEvolutionTuner'

experiment.config.tuner.class\_args = {'population\_size': 8}

Let’s launch the Experiment and analyze its results:

$ python3 ch3/tuners/custom\_tuner/run\_experiment.py

Figur[e 3-28 sho](#index_split_001.html#p168)ws the locations visited by the NewEvolutionTuner population. We see that the population has found the global function’s maxima and began to explore it.

154

![](index-168_1.png)

![](index-168_2.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-28.** Locations visited by population of NewEvolutionTuner*

Trial Metric panel in Figure [3-29 demons](#index_split_001.html#p168)trates the “hill-climbing” approach in action. The main problem with this approach is that it quickly finds a local maxima and stops exploring other search space areas.

***Figure 3-29.** Trial Metric panel*

Of course, developing a custom Tuner is not always an easy task. Still, the ability to implement your search algorithm and integrate it into the HPO process can greatly increase the experiment results. In this section, we have provided an example of how you can do this. If necessary, you can implement your ideas based on the illustration given in this section.

155

![](index-169_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

**Early Stopping**

Some parameters in the search space produce very low Trial results. And this is normal because the Tuner may not always know in advance which areas of the search space to explore and which not to explore. Tuner often tries parameters that give very low results. The Trial itself is expensive because a lot of time is spent on it. For example, training a neural network with a complex architecture on a large dataset can take hours. And it would be helpful not to spend a lot of time on trials that show poor results in their execution. NNI uses Early Stopping algorithms to solve that issue. Early Stopping algorithms analyze the intermediate trial results and compare them with the intermediate results of other trials. If the algorithm decides that the intermediate results of the current Trial are too low, then it stops the Trial so as not to waste time on it.

Figur[e 3-30 expl](#index_split_001.html#p169)ains Early Stopping approach. Trial 3 early stopped at step N

because intermediate results of this Trial were significantly worse than the other trials’

intermediate results at step N.

***Figure 3-30.** HPO Early Stopping*

156

![](index-170_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

The deep learning training algorithms also have Early Stop policies. Training Early Stopping policу stops model training when the model starts to degrade or there is no improvement for a long time. Do not confuse Training Early Stopping with HPO Early Stopping. They are not related in any way. Indeed, take a look at Figure [3-31](#index_split_001.html#p170). Training progress is good, and there is no reason to stop the training. But if we compare the training process with other trials, it is apparent that it is much worse, and the HPO Early Stopping algorithm can stop this Trial.

***Figure 3-31.** HPO Early Stopping vs. Training Early Stopping*

And Figure [3-32 demons](#index_split_001.html#p171)trates the opposite situation. The training process begins to degrade, and the Training Early Stopping algorithm terminates the training process.

In contrast, the HPO Early Stopping algorithm may consider the current Trail very promising because its intermediate results are significantly superior compared to other trials.

157

![](index-171_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-32.** HPO Early Stopping vs. Training Early Stopping*

Please keep in mind designing a deep learning model and the HPO Experiment that

Training Early Stopping and HPO Early Stopping are not correlated.

**Median Stop**

Median Stop is a straightforward, early stopping rule that stops a pending Trial after step N if the Trial’s best objective value by step N is strictly worse than the median value of the running averages of all completed trials’ objectives reported up to step N.

Median Stop algorithm can be implemented in Experiment with the following

experiment configuration:

assessor:

name: Medianstop

classArgs:

\# number of warm up steps

start\_step: 10

158

Chapter 3 hyperparameter OptimizatiOn Under Shell

Let’s look at a synthetic problem to see the Median Stop algorithm in action. Say, we have the following identity function, f: x → x, with the training progress containing 100

*x*

epochs (steps) and expressed by the following rule:

*epoch* + *r,* where *r* is a random

10

variable on (-1, 1) *.* We can characterize the function f as an identity function with parabolic training progress. Listing [3-14 con](#index_split_001.html#p172)tains the implementation of function f.

***Listing 3-14.*** Identity function with parabolic training progress. ch3/early\_stop/

medianstop/model.py

import random

def identity\_with\_parabolic\_training(x):

history = \[

max(round(x / 10, 2) \* pow(h, .5) + random.uniform(-3, 3), 0)

for h in range(1, 101)

\]

return x, history

Let’s visualize the training process of the following set of functions: f(0), f(10), f(20),

..., f(100).

if \_\_name\_\_ == '\_\_main\_\_':

import matplotlib.pyplot as plt

for x in range(0, 101, 10):

final, history = identity\_with\_parabolic\_training(x)

plt.plot(history, label = str(x))

plt.ylabel('Intermediate Result')

plt.xlabel('Epochs')

plt.legend()

plt.show()

Figur[e 3-33 sho](#index_split_001.html#p173)ws various training curves. This plot illustrates that the lower training curves are unpromising. Unpromising training can be stopped in advance according to the Early Stopping algorithm.

159

![](index-173_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-33.** Parabolic training*

Let’s launch an experiment that will use the Median Stop algorithm. The trial script is defined in Listing [3-15](#index_split_001.html#p173).

Trial header with imported modules:

***Listing 3-15.*** Median Stop Trial. ch3/early\_stop/medianstop/trial.py import os

import sys

from time import sleep

import nni

\# For NNI use relative import for user-defined modules

SCRIPT\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_)) + '/../../..'

sys.path.append(SCRIPT\_DIR)

Executing Trial:

from ch3.early\_stop.medianstop.model import identity\_with\_parabolic\_training

if \_\_name\_\_ == '\_\_main\_\_':

params = nni.get\_next\_parameter()

x = params\['x'\]

160

Chapter 3 hyperparameter OptimizatiOn Under Shell

final, history = identity\_with\_parabolic\_training(x)

for h in history:

sleep(.1)

nni.report\_intermediate\_result(h)

nni.report\_final\_result(final)

Listin[g 3-16 defines the E](#index_split_001.html#p174)xperiment with Median Stop algorithm.

***Listing 3-16.*** Experiment with Median Stop Algorithm. ch3/early\_stop/

medianstop/config.yml

searchSpace:

x:

\_type: quniform

\_value: \[1, 100, 0.1\]

maxTrialNumber: 100

trialConcurrency: 8

trialCodeDirectory: .

trialCommand: python3 trial.py

tuner:

name: Random

assessor:

name: Medianstop

classArgs:

\# number of warm up steps

start\_step: 10

trainingService:

platform: local

Now we are ready to run the Experiment:

nnictl create --config ch3/early\_stop/medianstop/config.yml

161

![](index-175_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

After the experiment is completed, we can observe in Figure [3-34 th](#index_split_001.html#p175)at many trials have the EARLY\_STOPPED status, as expected.

***Figure 3-34.** Trials detail panel*

**Curve Fitting**

Curve Fitting Assessor is an LPA (learning, predicting, assessing) algorithm that stops a pending Trial at step *N* if the prediction of the final epoch’s performance is worse than the best final performance in the trial history. Curve Fitting Assessor makes a prediction about the final result of the Trial’s training and compares it with the completed ones.

This algorithm treats the Early Stopping task as a time series forecasting problem. If the training prediction is pessimistic, then the algorithm stops the trial. Figur[e 3-35](#index_split_001.html#p176) explains the Curve Fitting Early Stopping approach.

162

![](index-176_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-35.** Curve Fitting prediction*

Curve Fitting algorithm can be implemented in Experiment with the following

experiment configuration:

assessor:

name: Curvefitting

classArgs:

epoch\_num: 20

start\_step: 6

threshold: 0.95

gap: 1

We will not study the principles of the Curve Fitting Early Stopping algorithm in this book. You can refer to the official documentation ([https://nni.readthedocs.](https://nni.readthedocs.io/en/v2.7/reference/hpo.html#nni.algorithms.hpo.curvefitting_assessor.CurvefittingAssessor)

[io/en/v2.7/reference/hpo.html#nni.algorithms.hpo.curvefitting\_assessor.](https://nni.readthedocs.io/en/v2.7/reference/hpo.html#nni.algorithms.hpo.curvefitting_assessor.CurvefittingAssessor)

[CurvefittingAssessor](https://nni.readthedocs.io/en/v2.7/reference/hpo.html#nni.algorithms.hpo.curvefitting_assessor.CurvefittingAssessor)) or review a paper dedicated to “Speeding up Automatic Hyperparameter Optimization of Deep Neural Networks by Extrapolation of Learning Curves” ([https://ml.informatik.uni-freiburg.de/wp-content/uploads/papers/](https://ml.informatik.uni-freiburg.de/wp-content/uploads/papers/15-IJCAI-Extrapolation_of_Learning_Curves.pdf)

[15-IJCAI-Extrapolation\_of\_Learning\_Curves.pdf](https://ml.informatik.uni-freiburg.de/wp-content/uploads/papers/15-IJCAI-Extrapolation_of_Learning_Curves.pdf)).

**Risk to Stop a Good Trial**

The Early Stopping algorithm can significantly speed up the completion of an

experiment and save computational resources. But there is always a risk of stopping a good trial too early, which would probably mean rejecting very good parameters in the search space. Look at Figur[e 3-36](#index_split_001.html#p177), early stopped trial could show good performance.

163

![](index-177_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-36.** Good trial early stopped*

However, there is a very tiny chance of stopping a trial that can give good results too early. Usually, the training curves of deep learning models behave similarly, so if the trials’ intermediate results were significantly worse than those of other trials, you probably should not expect anything good, but complete the trial and move on to the next one.

**Searching for Optimal Functional Pipeline**

**and Classical AutoML**

Libraries: Scikit-learn

Let’s go back to the problem we studied in the “From LeNet to AlexNet” section

of Chapt[er 2. I](https://doi.org/10.1007/978-1-4842-8149-9_2)n this task, we built a functional pipeline that would optimally solve the image classification problem. Indeed, each layer of deep learning is a particular functional operator, and we tried to find the best pipeline of these operators using the HPO approach. Figur[e 3-37 pr](#index_split_001.html#p178)esents neural network architecture as a functional pipeline.

164

![](index-178_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-37.** Neural network architecture as functional pipeline*

Let’s convert the problem into a more strict mathematical language. We need

to find a model *M* that consists of compositions of functions *Fi* ∈ { *F*} and maximizes the value *L*( *M*, *D*), where *L* evaluates the performance of model *M* on dataset *D*. *Figure [3-38](#index_split_001.html#p179)* *formulates the optimal functional pipeline problem:* 165

![](index-179_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-38.** Optimal functional pipeline problem*

Let’s study how this problem can be solved with NNI. As an example, I want to use the classic AutoML task, which searches for the optimal pipeline of classical shallow machine learning methods to solve a supervised learning problem. In this section, I would like to pay tribute to classical machine learning, which increasingly gives way to deep learning. This approach can be applied to any problem of searching the optimal functional pipeline.

**Problem**

Let’s examine binary classification problem with Gamma Telescope Datas[et (https://](https://archive.ics.uci.edu/ml/datasets/magic+gamma+telescope)

[archive.ics.uci.edu/ml/datasets/magic+gamma+telescope](https://archive.ics.uci.edu/ml/datasets/magic+gamma+telescope)). This dataset contains data of signals received by the telescope. The task is to discriminate signals caused by primary **gammas** (signal) from the images of **hadronic** showers initiated by cosmic rays in the upper atmosphere (background). This dataset contains 19020 instances and the following columns:

1\. fLength: Type: real. Major axis of ellipse (mm)

2\. fWidth: Type: real. Minor axis of ellipse (mm\])

3\. fSize: Type: real. 10-log of sum of content of all pixels (photons)

4\. fConc: Type: real. Ratio of sum of two highest pixels over

fSize (ratio)

5\. fConc1: Type: real. Ratio of highest pixel over fSize (ratio)

6\. fAsym: Type: real. Distance from highest pixel to center, projected

onto major axis (mm)

166

Chapter 3 hyperparameter OptimizatiOn Under Shell

7\. fM3Long: Type: real. Third root of third moment along major

axis (mm)

8\. fM3Trans: Type: real. Third root of third moment along minor

axis (mm)

9\. fAlpha: Type: real. Angle of major axis with vector to origin (deg)

10\. fDist: Type: real. Distance from origin to center of ellipse (mm)

11\. class: Values: 'g', 'h'. Gamma (signal), Hadron (background).

g = gamma (signal): 12332. h = hadron (background): 6688

Perhaps the reader understands something in these physical data, but I do not

understand anything about them. But that’s exactly what we need machine learning for –

to find patterns and dependencies where we cannot see them ourselves.

The dataset is located in ch3/ml\_pipeline/data/magic04.data and is converted to a supervised learning problem in Listing [3-17](#index_split_001.html#p180).

Importing modules:

***Listing 3-17.*** Gamma Telescope Dataset. ch3/ml\_pipeline/utils.py import os

from sklearn.model\_selection import train\_test\_split

import pandas as pd

import numpy as np

def telescope\_dataset():

Loading dataset from the file:

cd = os.path.dirname(os.path.abspath(\_\_file\_\_))

telescope\_df = pd.read\_csv(f'{cd}/data/magic04.data')

Dropping na values:

telescope\_df.dropna(inplace = True)

Setting column names:

telescope\_df.columns = \[

'fLength', 'fWidth', 'fSize', 'fConc', 'fConcl',

'fAsym', 'fM3Long', 'fM3Trans', 'fAlpha', 'fDist', 'class'\]

167

Chapter 3 hyperparameter OptimizatiOn Under Shell

Shuffling dataset:

telescope\_df = telescope\_df.iloc\[np.random.

permutation(len(telescope\_df))\]

telescope\_df.reset\_index(drop = True, inplace = True)

Class labeling:

telescope\_df\['class'\] = telescope\_df\['class'\].map({'g': 0, 'h': 1})

y = telescope\_df\['class'\].values

Splitting dataset on train and test datasets:

train\_ind, test\_ind = train\_test\_split(

telescope\_df.index,

stratify = y,

train\_size = 0.8,

test\_size = 0.2

)

X\_train = telescope\_df.drop('class', axis = 1).loc\[train\_ind\].values

X\_test = telescope\_df.drop('class', axis = 1).loc\[test\_ind\].values

y\_train = telescope\_df.loc\[train\_ind, 'class'\].values

y\_test = telescope\_df.loc\[test\_ind, 'class'\].values

return X\_train, y\_train, X\_test, y\_test

Since we have identified the problem and prepared the dataset, we can begin to

determine the machine learning methods that our model will consist of.

**Operators**

Now let’s define the functions that will make up the functional pipeline. We will call them Operators in the machine learning context. Machine learning operators for a classification problem can be separated into three types:

• **Selectors**: Choose the most significant features (columns) from the

dataset, removing dependent features. Usually reduces the input size.

The selected features remain unchanged.

168

![](index-182_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

• **Transformers**: Convert input according to some mathematical

function without changing the input size.

• **Classifiers**: Solve the classification problem itself.

Figur[e 3-39 sho](#index_split_001.html#p182)ws a machine learning pipeline: selector, transformer, and classifier.

***Figure 3-39.** Machine learning operators: selector, transformer, and classifier* Each operator has its own parameters, such as max\_depth in the

DecisionTreeClassifier. Listin[g 3-18 cr](#index_split_001.html#p182)eates an operator space that will be used for the AutoML pipeline.

(Full code is provided in the corresponding file: *ch3/ml\_pipeline/operator.py*.) Each operator is an object that has a name, implementation, and parameters:

***Listing 3-18.*** Operator space

class Operator:

def \_\_init\_\_(self, name, clz, params = None):

if params is None:

params = {}

self.name = name

self.clz = clz

self.params = params

169

Chapter 3 hyperparameter OptimizatiOn Under Shell

Next, we define the operator space:

class OperatorSpace:

Selector list:

selectors = \[

Operator('SelectFwe', SelectFwe, {

'alpha': arange(0, 0.05, 0.001).tolist()

}),

Operator('SelectPercentile', SelectPercentile, {

'percentile': list(range(1, 100))

}),

(For full selector list, please refer to the source code.)

Transformer list:

transformers = \[

Operator('Binarizer', Binarizer, {

'threshold': arange(0.0, 1.01, 0.05).tolist()

}),

Operator('FastICA', FastICA, {

'tol': arange(0.0, 1.01, 0.05).tolist()

}),

(For full transformer list, please refer to the source code.)

Classifier list:

classifiers = \[

Operator('GaussianNB', GaussianNB),

Operator('BernoulliNB', BernoulliNB, {

'alpha': \[0.01, 0.1, 1, 10\]

}),

(For full classifier list, please refer to the source code.)

170

Chapter 3 hyperparameter OptimizatiOn Under Shell

Finally, we add an additional auxiliary method get\_operator\_by\_name, which

returns the operator by its name:

@classmethod

def get\_operator\_by\_name(cls, name):

operators = cls.selectors + cls.transformers + cls.classifiers

for o in operators:

if o.name == name:

return o

return None

**Search Space**

Let’s define search space for the classifier. We assume that the classifier’s operator pipeline will have

• **Selectors**: From 0 to 1 (selector is advised but not required)

• **Transformers**: From 0 to 3 (selector is advised but not required)

• **Classifier**: 1 (is required)

Therefore, a pipeline can have from one to five operators. Please take a look at Figur[e 3-40.](#index_split_001.html#p185)

171

![](index-185_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Figure 3-40.** Pipeline cells*

The pipeline has five cells. Each cell can be filled with some value from the

corresponding operator space. The cell can be empty if none value is selected. For example, the following pipeline might be selected: Selector3 → none → Transformer1

→ none → Classifier2, which is equal to Selector3 → Transformer1 → Classifier2.

This search space definition is huge and challenging to construct manually, so we will add a special class in Listin[g 3-19](#index_split_001.html#p186) that will create an operator search space definition according to the NNI specification.

172

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Listing 3-19.*** Search space. ch3/ml\_pipeline/search\_space.py

from ch3.ml\_pipeline.operator import OperatorSpace

class SearchSpace:

Each cell has an operator type that can be filled by selector, transformer, and

classifier. The operator\_search\_space method creates a search space for each

cell type.

@classmethod

def **operator\_search\_space**(cls, operator\_type):

"""

Search space for operator by òperator\_typè

"""

ss = \[\]

operators = \[\]

if operator\_type == 'selector':

\# Selectors are not required in Pipeline

ss.append({'\_name': 'none'})

operators = OperatorSpace.selectors

elif operator\_type == 'transformer':

\# Transformers are not required in Pipeline

ss.append({'\_name': 'none'})

operators = OperatorSpace.transformers

elif operator\_type == 'classifier':

operators = OperatorSpace.classifiers

for o in operators:

row = {'\_name': o.name}

for p\_name, values in o.params.items():

row\[p\_name\] = {"\_type": "choice", "\_value": values}

ss.append(row)

return ss

173

Chapter 3 hyperparameter OptimizatiOn Under Shell

Next, we define a method build that constructs a search space of all cells according to the NNI specification:

@classmethod

def **build**(cls):

return {

"op\_1": {

"\_type": "choice",

"\_value": cls.operator\_search\_space('selector')

},

"op\_2": {

"\_type": "choice",

"\_value": cls.operator\_search\_space('transformer')

},

"op\_3": {

"\_type": "choice",

"\_value": cls.operator\_search\_space('transformer')

},

"op\_4": {

"\_type": "choice",

"\_value": cls.operator\_search\_space('transformer')

},

"op\_5": {

"\_type": "choice",

"\_value": cls.operator\_search\_space('classifier')

}

}

Even though the search space definition is quite large, we can print it out:

if \_\_name\_\_ == '\_\_main\_\_':

search\_space = SearchSpace.build()

print(search\_space)

We will use dynamic search space construction to launch the experiment in

embedded mode, although this technique can also be applied to build a static JSON file.

174

Chapter 3 hyperparameter OptimizatiOn Under Shell

**Model**

So, what do we have by now? We have an operator space and a search space. Let’s now implement a model that converts the pipeline configuration into a real machine learning classifier. Listin[g 3-20 in](#index_split_001.html#p188)troduces MlPipelineClassifier.

Importing modules:

***Listing 3-20.*** MlPipelineClassifier. ch3/ml\_pipeline/model.py

from sklearn.pipeline import Pipeline

from ch3.ml\_pipeline.operator import OperatorSpace

from ch3.ml\_pipeline.utils import telescope\_dataset

class MlPipelineClassifier:

Model receives pipeline configuration and converts it to the actual Scikit-learn pipeline:

def **\_\_init\_\_**(self, pipe\_config):

ops = \[\]

for \_, params in pipe\_config.items():

\# operator name

op\_name = params.pop('\_name')

\# skips 'none' operator

if op\_name == 'none':

continue

op = OperatorSpace.get\_operator\_by\_name(op\_name)

ops.append((op.name, op.clz(\*\*params)))

self.pipe = Pipeline(ops)

Model training method:

def **train**(self, X, y):

self.pipe.fit(X, y)

175

Chapter 3 hyperparameter OptimizatiOn Under Shell

Computing the accuracy:

def **score**(self, X, y):

return self.pipe.score(X, y)

Since the model is ready, let’s try to initialize it using the sample pipeline parameter and apply it to the classification problem:

if \_\_name\_\_ == '\_\_main\_\_':

pipe\_config = {

'op\_1': {

'\_name': 'SelectPercentile',

'percentile': 2

},

'op\_2': {

'\_name': 'none'

},

'op\_3': {

'\_name': 'Normalizer',

'norm': 'l1'

},

'op\_4': {

'\_name': 'PCA',

'svd\_solver': 'randomized',

'iterated\_power': 3

},

'op\_5': {

'\_name': 'DecisionTreeClassifier',

'criterion': "entropy",

'max\_depth': 8

}

}

model = MlPipelineClassifier(pipe\_config)

X\_train, y\_train, X\_test, y\_test = telescope\_dataset()

176

Chapter 3 hyperparameter OptimizatiOn Under Shell

model.train(X\_train, y\_train)

score = model.score(X\_test, y\_test)

print(score)

The model demonstrates **64%** accuracy. This is definitely not the result we expect, so let’s use the HPO techniques to construct a better-performance model.

**Tuner**

Now everything is ready to start the experiment. But I would like to focus on the search space that we use. The trial parameter is a sequence of operators, which may contain empty operators, that is, S3(p3) → none → T1(p1) → none → C2(p2). But at the same time, the following parameter exists too: S3(p3) → none → none → T1(p1) → C2(p2).

They are different parameters in the search space but generate the same classifier model:

• S3(p3) → none → T1(p1) → none → C2(p2)

• S3(p3) → none → none → T1(p1) → C2(p2)

• S3(p3) → T1(p1) → C2(p2).

Keep in mind that the same two identical operators with different parameters are not equal, that is, SelectFwe(alpha=0) is not equal to SelectFwe(alpha=0.05). Let’s customize Tuner by forbidding it to create parameters that will generate equivalent models concerning the parameters already tried, that is, if we already tried parameter P1 = SelectPercentile(percentile = 2) → none → Normalizer(norm='l1')

→ none → DecisionTreeClassifier(max\_depth=8), then parameter P2 =

SelectPercentile(percentile = 2) → none → none → Normalizer(norm='l1')

→ DecisionTreeClassifier(max\_depth=8) will not be passed to Experiment,

because the model generated by P2 equals to the model generated by P1. Let’s

create EvolutionShrinkTuner, which inherits EvolutionTuner and tracks all

executed pipelines forbidding passing the equal ones to the Experiment. We can see EvolutionShrinkTuner implementation in Listing [3-21](#index_split_001.html#p191).

177

Chapter 3 hyperparameter OptimizatiOn Under Shell

***Listing 3-21.*** EvolutionShrinkTuner. ch3/ml\_pipeline/evolution\_shrink\_tuner.py import json

from nni.algorithms.hpo.evolution\_tuner import EvolutionTuner

class EvolutionShrinkTuner(EvolutionTuner):

def \_\_init\_\_(self, optimize\_mode = "maximize", population\_size = 32):

super().\_\_init\_\_(optimize\_mode, population\_size)

We define registry property that will track all created pipelines:

self.registry = \[\]

If the super().generate\_parameters method of the parent EvolutionTuner object

returns a parameter that has already been tried, then the super().generate\_parameters method is called again until a unique parameter is generated. Because EvolutionTuner has random behavior, super().generate\_parameters can be expected to return

different parameters on subsequent calls.

def **generate\_parameters**(self, \*args, \*\*kwargs):

params = super().generate\_parameters(\*args, \*\*kwargs)

\# If not \`paramsàre not valid generate new ones

while not self.is\_valid(params):

params = super().generate\_parameters(\*args, \*\*kwargs)

return params

The following is\_valid method converts the parameter to the canonical form by

removing none operators and checks if it has already been tried: if it has, then returns False; if not, then saves it and returns True.

def **is\_valid**(self, params):

\# All step names

step\_names = \[v\['\_name'\] for \_, v in params.items() if v\['\_name'\]

!= 'none'\]

\# No duplicates allowed

if len(step\_names) != len(set(step\_names)):

return False

178

Chapter 3 hyperparameter OptimizatiOn Under Shell

\# \`params\` to canonical string

canonical\_form = 'X'

for \_, step\_config in params.items():

if step\_config\['\_name'\] == 'none':

continue

canonical\_form += '--->' + json.dumps(step\_config)

\# If \`canonical\_formàlready tested

if canonical\_form in self.registry:

return False

self.registry.append(canonical\_form)

return True

This simple technique introduces the concept of equivalence between the elements of the search space and can significantly shrink the search space.

**Experiment**

And now, we are finally ready to launch an experiment to find the optimal functional pipeline for solving the AutoML problem. The trial script in Listin[g 3-22](#index_split_001.html#p192) initializes the model, prepares datasets, trains the model, tests it, and returns model accuracy to NNI Experiment.

(Full code is provided in the corresponding file: *ch3/ml\_pipeline/trial.py*.)

***Listing 3-22.*** Trial

def trial(hparams):

#Initializing model

model = MlPipelineClassifier(hparams)

\# Preparing dataset

X\_train, y\_train, X\_test, y\_test = telescope\_dataset()

model.train(X\_train, y\_train)

\# Calculating \`scoreòn test dataset

score = model.score(X\_test, y\_test)

179

Chapter 3 hyperparameter OptimizatiOn Under Shell

\# Send final score to NNI

nni.report\_final\_result(score)

Listin[g 3-23 p](#index_split_001.html#p193)uts everything together and runs the experiment.

Import modules:

***Listing 3-23.*** Optimal functional pipeline experiment. ch3/ml\_pipeline/

run\_experiment.py

from pathlib import Path

from nni.experiment import Experiment, CustomAlgorithmConfig

from ch3.ml\_pipeline.search\_space import SearchSpace

Common Experiment configuration:

experiment = Experiment('local')

experiment.config.experiment\_name = 'AutoML Pipeline'

experiment.config.trial\_concurrency = 4

experiment.config.max\_trial\_number = 500

Generating search space:

experiment.config.search\_space = SearchSpace.build()

Trial configuration:

experiment.config.trial\_command = 'python3 trial.py'

experiment.config.trial\_code\_directory = Path(\_\_file\_\_).parent

Setting the custom EvolutionShrinkTuner:

experiment.config.tuner = CustomAlgorithmConfig()

experiment.config.tuner.code\_directory = Path(\_\_file\_\_).parent

experiment.config.tuner.class\_name = 'evolution\_shrink\_tuner.

EvolutionShrinkTuner'

experiment.config.tuner.class\_args = {

'optimize\_mode': 'maximize',

'population\_size': 64

}

180

![](index-194_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

Launching Experiment:

http\_port = 8080

experiment.start(http\_port)

\# Event Loop

while True:

if experiment.get\_status() == 'DONE':

search\_data = experiment.export\_data()

search\_metrics = experiment.get\_job\_metrics()

input("Experiment is finished. Press any key to exit...")

break

Figur[e 3-41 sho](#index_split_001.html#p194)ws top trials of the AutoML Experiment.

***Figure 3-41.** AutoML Experiment best Trials*

181

Chapter 3 hyperparameter OptimizatiOn Under Shell

The best Trial demonstrates **0.89143** accuracy and has the following parameters:

{

"op\_1": {

"\_name": "SelectFwe",

"alpha": 0.049

},

"op\_2": {

"\_name": "MinMaxScaler"

},

"op\_3": {

"\_name": "RobustScaler"

},

"op\_4": {

"\_name": "none"

},

"op\_5": {

"\_name": "MLPClassifier",

"alpha": 0.01,

"learning\_rate\_init": 0.01

}

}

The best Trial can be converted to the functional pipeline:

X → Select(alpha=0.049) → MinMaxScaler → RobustScaler →

MLPClassifier(alpha=0.01, learning\_rate\_init=0.01) → Y

In fact, the classifier we have built shows very good results, which are close to optimal.

The best classifier for this model performs with the following accuracy: 0.898 (“Multi-Task Architecture with Attention for Imaging Atmospheric Cherenkov Telescope Data Analysis, [” *www.scitepress.org/Papers/2021/102974/102974.pdf*](http://www.scitepress.org/Papers/2021/102974/102974.pdf)). We have just built the custom AutoML toolkit based on NNI. This approach can also be applied to any functional pipeline optimization. Similarly, you can automatically design deep learning models with a sequential layer layout. Indeed, operator space can consist of deep learning layers, and the model can be a neural network based on the sequence of layers pipeline. Of course, we could dive deeper into applying this approach to Neural Architecture Search, but it has significant drawbacks, which we will discuss in the next section.

182

![](index-196_1.png)

Chapter 3 hyperparameter OptimizatiOn Under Shell

**Limits of HPO Applying to Neural Architecture Search**

The approach described in this section can be successfully applied to the search for neural network architectures but with a significant limitation. Using HPO techniques described in this section, we can only get an architecture with a sequential layer stack, that is, an architecture in which each layer connects to another one sequentially. This is a significant limitation since many modern neural network architectures use multiple connections between their layers, as shown in Figur[e 3-42.](#index_split_001.html#p196)

***Figure 3-42.** Multi-connected neural network*

We need some different and special techniques to search for efficient neural network architectures. And we will begin to explore them in the next chapter.

**Hyperparameters for Hyperparameter Optimization**

When we talked about automated deep learning, we mentioned that AutoDL solves

the problem of finding optimal architectures and hyperparameters. But each AutoDL

technique has many parameters on its own! For example, we need to define the search space, a maximum number of trials, find a suitable Tuner, define Tuner parameters, etc.

It turns out that the problem that solves the hyperparameter selection problem itself has even more hyperparameters! What is the point of using the HPO approach and

other AutoDL methods then? This is a fair question. The answer is that even a poorly configured HPO Experiment produces a significantly better model than a model with 183

Chapter 3 hyperparameter OptimizatiOn Under Shell

a poorly configured architecture or hyperparameters. We can never be sure in advance what the best settings for an AutoDL method are. However, we can be confident that the AutoDL method will surely produce a model close to the optimal one and significantly better than the one we would build manually.

**Summary**

This chapter has taken a deep dive into Tuner internals and various black-box function optimization algorithms. Understanding the principles of Tuners’ behavior and their practical application can remarkably improve the design of NNI experiments and HPO

results. In the next chapter, we’ll move on to the most exciting and interesting part of our book: Neural Architecture Search. We will study the latest techniques to find the optimal design of neural networks for a specific task.

184

**CHAPTER 4**

**Multi-trial Neural**

**Architecture Search**

And now we come to the most exciting part of this book. As we noted at the end of the last chapter, HPO methods are pretty limited for automating the search for the optimal deep learning models, but **Neural Architecture Search** (**NAS**) dispels these limits. This chapter focuses on NAS, one of the most promising areas of automated deep learning. Automatic Neural Architecture Search is increasingly important in finding appropriate deep learning models. Recent researches have proven the NAS effectiveness and found some models that could beat manually tuned ones. NAS is a fairly young discipline in machine learning.

It took shape as a separate discipline in 2018. Since then, it has made a significant breakthrough in automating neural network architecture construction that solves a specific problem. The most manual design of neural networks can be replaced by automated

architecture search soon, so this area is very up and coming for all data scientists. NAS

produced many top computer vision architectures. Architectures like NASNet, EfficientNet, and MobileNet are the result of automated Neural Architecture Search.

There are two types of NAS: ***Multi-trial*** and ***One-shot***. In Multi-trial NAS, a model evaluator evaluates each sampled model’s performance, and an Exploration Strategy samples models from defined Model Space, while One-shot NAS tries to find optimal neural architecture training and exploring one Supernet derived from the Model Space.

This chapter is dedicated to Multi-trial NAS.

This chapter is divided into two parts: ***Neural Architecture Search Using Retiarii***

***(PyTorch)*** and ***Classic Neural Architecture Search (TensorFlow)***. ***Retiarii*** is a deep learning framework that supports the exploratory training on a neural network Model Space developed by NNI experts. Retiarii is an advantageous approach that allows structuring and planning the NAS. Unfortunately, the NNI 2.7 version (which is used in this book) only implements the Retiarii approach for the PyTorch framework. And it would be unfair not to pay attention to the TensorFlow framework in this chapter, so 185

© Ivan Gridin 2022

I. Gridin, *Automated Deep Learning Using Neural Network Intelligence*,

[https://doi.org/10.1007/978-1-4842-8149-9\_4](https://doi.org/10.1007/978-1-4842-8149-9_4#DOI)

![](index-199_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

the classic methods of NAS using NNI are considered in the *Classic Neural Architecture* *Search (TensorFlow)* part. In any case, NNI supports TensorFlow for One-shot NAS, which we will explore in the next chapter. Therefore, TensorFlow users will be able to take full advantage of NAS approaches.

**Neural Architecture As Data Flow Graph**

We will begin this chapter by defining how the NAS perceives the neural network

architecture. Neural architecture is considered as a Data Flow Graph (DFG). DFG is a collection of nodes and connections between them. DFG displays the data transfer from one node to another. Each node has its own type and parameters. Figur[e 4-1](#index_split_001.html#p199)

demonstrates an example of DFG.

***Figure 4-1.** Data Flow Graph*

186

Chapter 4 Multi-trial Neural arChiteCture SearCh

In Figur[e 4-1, w](#index_split_001.html#p199)e see the DFG, which contains different types of nodes with parameters. The architecture of each neural network can be represented as a Data Flow Graph. Indeed, in Figur[e 4-1, w](#index_split_001.html#p199)e can replace the rectangle node with a convolution layer with parameters: padding, stride, filter\_size, etc. Neural Architecture Search Explorers have no idea about the nature of each of the DFG nodes. The main task is to construct a DFG from various deep learning layers, which forms the architecture of a neural network and solves a specific problem in the best way.

**Neural Architecture Search Using Retiarii (PyTorch)**

Retiarii is the framework developed by NNI experts, and it is the first framework that supports deep learning exploratory training. Exploratory training implies that different deep neural networks (DNNs) training results are shared. This approach compares

training of different models, performs optimization, and stops unpromising models with poor intermediate results. Also, Retiarii provides a new interface to specify a deep learning Model Space for exploration and an interface to describe the Exploration Strategy that decides the order to instantiate and train models in, prioritize model training, and stop the training of certain models. Retiarii identifies the correlations between the instantiated models and develops a set of cross-model optimizations to improve the overall exploratory training process. You can read more information about the Retiarii framework in the following artic[le: www.usenix.org/system/files/osdi20-](http://www.usenix.org/system/files/osdi20-zhang_quanlu.pdf)

[zhang\_quanlu.pdf](http://www.usenix.org/system/files/osdi20-zhang_quanlu.pdf).

NNI version 2.7 has a PyTorch-only implementation of the Retiarii

framework. In the next NNI releases, the TensorFlow implementation should

be added. Please refer to the official documentation to check the actual state:

[https://nni.readthedocs.io/en/v2.7/nas/overview.html](https://nni.readthedocs.io/en/v2.7/nas/overview.html).

187

Chapter 4 Multi-trial Neural arChiteCture SearCh

**Introduction to NAS Using Retiarii**

The best way to dive into NAS using Retiarii is to examine a simple example of finding the optimal DFG for a particular task. We will not go deep into the design of neural networks but will focus on a simple arithmetic problem. Suppose we have some chain of operators *F*, which performs the following actions:

x = 1

x ← x × 2

x ← x × 4

return x

We can enrich the chain *F* with the following statements:

x = 1

x ← sigmoid(x) or x ← tanh(x) or x ← relu(x)

x ← x × 2

x ← x + 0 or x ← x + 1 or x ← x + 2

x ← x × 4

x ← sigmoid(x) or x ← tanh(x) or x ← relu(x)

return x

The Model Space of this problem can be depicted as shown in Figure [4-2](#index_split_001.html#p202). We need to find a DFG that maximizes output.

188

![](index-202_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-2.** Data Flow Graph Model Space*

Of course, this is a trivial task, but it is well suited as an introductory example of using the Retiarii framework in NNI. Let’s move on to solving this problem.

Listin[g 4-1](#index_split_001.html#p202) defines the Model Space.

We import common modules:

***Listing 4-1.*** Model Space. ch4/retiarii/intro/dummy\_model.py

import os

import torch

import nni

Retiarii uses import nni.retiarii.nn.pytorch as nn for PyTorch. It is very

important to use layers from this package implementing NAS for PyTorch.

**import nni.retiarii.nn.pytorch as nn**

189

Chapter 4 Multi-trial Neural arChiteCture SearCh

First, we need to define the Model Space for Exploration. Model Space in the

NAS context can be considered as search space in the HPO context. Model Space is represented by a class that contains all possible architectures to try. Each such class must be annotated with @model\_wrapper.

from nni.retiarii import model\_wrapper

**@model\_wrapper**

class DummyModel(nn.Module):

def \_\_init\_\_(self):

super().\_\_init\_\_()

Different variants of the neural network architecture are determined by special

methods called *Mutators*. Mutators define the rules for different variations or mutations of the model. The LayerChoice mutator defines different layer choices. In the following, LayerChoice selects one of three layers: Tanh, Sigmoid, and ReLU:

\# operator 1

self.op1 = nn.LayerChoice(\[

nn.Tanh(),

nn.Sigmoid(),

nn.ReLU()

\])

Another type of mutation is ValueChoice. This mutator selects one of the values from the list:

\# addition

self.add = nn.ValueChoice(\[0, 1, 2\])

Next, we define the LayerChoice mutator again:

\# operator 2

self.op2 = nn.LayerChoice(\[

nn.Tanh(),

nn.Sigmoid(),

nn.ReLU()

\])

190

Chapter 4 Multi-trial Neural arChiteCture SearCh

Finally, we chain all operators together, as shown in Figur[e 4-2:](#index_split_001.html#p202)

def forward(self, x):

x = self.op1(x)

x = x \* 2

x += self.add

x = x \* 4

x = self.op2(x)

return x

After, we define the evaluate method, which returns the model result:

def evaluate(model\_cls):

Evaluating the model:

model = model\_cls()

x = torch.Tensor(\[1\])

y = model(x)

This code is used for model architecture visualization. We will get back to this technique later.

onnx\_dir = os.path.abspath(os.environ.get('NNI\_OUTPUT\_DIR', '.'))

os.makedirs(onnx\_dir, exist\_ok = True)

torch.onnx.export(model, x, onnx\_dir + '/model.onnx')

Returning the result:

nni.report\_final\_result(y.item())

Once we have defined the Model Space and its instance Evaluation, we can move on to launching the experiment with the code shown in Listin[g 4-2.](#index_split_001.html#p204)

Importing necessary modules:

***Listing 4-2.*** Retiarii Experiment. ch4/retiarii/intro/run\_experiment.py from time import sleep

from nni.retiarii.evaluator import FunctionalEvaluator

from nni.retiarii.experiment.pytorch import RetiariiExperiment, RetiariiExeConfig import nni.retiarii.strategy as strategy

from ch4.retiarii.intro.dummy\_model import DummyModel, evaluate

191

Chapter 4 Multi-trial Neural arChiteCture SearCh

There are seven main steps to launch the Retiarii Experiment:

1\. We set the Model Space:

model\_space = DummyModel()

2\. We define the Evaluator, which evaluates model instance:

evaluator = FunctionalEvaluator(evaluate)

3\. Next, we chose a Search Strategy that explores the Model Space:

search\_strategy = strategy.Random(dedup = True)

4\. We initialize the Retiarii Experiment with defined Model Space,

Evaluator, and Search Strategy:

exp = RetiariiExperiment(model\_space, evaluator, \[\], search\_

strategy)

5\. Setting Experiment configuration:

exp\_config = RetiariiExeConfig('local')

exp\_config.experiment\_name = 'dummy\_search'

exp\_config.trial\_concurrency = 1

exp\_config.max\_trial\_number = 100

exp\_config.training\_service.use\_active\_gpu = False

export\_formatter = 'dict'

6\. Launching Experiment:

exp.run(exp\_config, 8080)

7\. Returning best results. We can analyze the Experiment’s results in

WebUI before exit:

while True:

sleep(1)

input("Experiment is finished. Press any key to exit...")

print('Final model:')

192

![](index-206_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

for model\_code in exp.export\_top\_models(formatter =

export\_formatter):

print(model\_code)

break

After the experiment is completed, we can analyze the Trial jobs panel examining the best results.

***Figure 4-3.** Trial jobs panel*

As shown in Figur[e 4-3](#index_split_001.html#p206), the best model returns 16. And it has the following set of parameters:

{

"model\_1": "2",

"model\_2": 2,

"model\_3": "2"

}

193

![](index-207_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

The preceding parameters are not self-describing, so we can use the visualization function to render DFG render as shown in Figur[e 4-4.](#index_split_001.html#p207)

***Figure 4-4.** Visualization panel*

NNI uses Netron to visualize trial models. Netron is a tiny viewer for neural networks, deep learning, and machine learning models. Clicking the Netron button, you’ll see the screen as shown in Figure [4-5](#index_split_001.html#p208).

194

![](index-208_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-5.** Netron model visualization*

Now we can declare that we have found a solution to the problem of finding a model that maximizes the value of the chain of operators *F*. The Data Flow Graph of this model is shown in Figure [4-6](#index_split_001.html#p209).

195

![](index-209_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-6.** Best Data Flow Graph in Model Space*

The purpose of this example was to demonstrate that the primary goal of a NAS

approach is to find a DFG that maximizes (or minimizes) a black-box function. In the same way HPO methods are searching for parameters that maximize (or minimize)

the black- box function. After introducing basic NAS techniques, we can dive into more details.

**Retiarii Framework**

Retiarii framework is designed to separate the main logical entities of Neural

Architecture Search. This makes the NAS procedure clear and elegant. Using the Retiarii framework, the researcher can only focus on particular aspects of the investigation. The main components of the Retiarii framework are

196

Chapter 4 Multi-trial Neural arChiteCture SearCh

• Base Model

• Mutator

• Model Space

• Evaluator

• Exploration Strategy

*Base Model* is the primary skeleton of a neural network. Base Model is actually a simple deep learning model that solves some problem. Often the Base Model does

not show good performance. But it has some primary neural architecture and training algorithm.

*Mutator* is a possible change that a Base Model can be subjected to. Mutator defines the transformation of the Base Model architecture into another one. Usually, many mutators are applied to Base Model.

*Model Space* is the set of all possible Base Model mutations. Each mutator generates several variants of neural network architectures. Applying all mutators to the Base Model defines the Model Space.

*Evaluator* measures the performance of a sample from the Model Space. This is a typical algorithm for training and testing a neural network.

*Exploration Strategy* defines the Model Space exploration algorithm. The main objective of the Exploration Strategy is to find the best model in the least number of trials.

All these concepts are pretty familiar to us after studying Hyperparameter

Optimization. Table [4-1](#index_split_001.html#p210) contains the main logical entities from NAS and HPO. As you can see, they mean almost the same thing.

***Table 4-1.** NAS and HPO logical entities*

**NAS**

**HPO**

Base Model + Mutator

Search space type

Model Space

Search space

evaluator

trial

exploration Strategy

tuner

197

![](index-211_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

Figur[e 4-7 illus](#index_split_001.html#p211)trates the relationship of various components in the Retiarii framework.

***Figure 4-7.** Retiarii framework*

Let’s go ahead and look at each of these components in detail.

**Base Model**

The Base Model is a starting point from which all possible architecture modifications will be made. For example, the Base Model for NAS of the MNIST problem can be presented as it is shown in Listing [4-3.](#index_split_001.html#p211)

Importing PyTorch modules:

***Listing 4-3.*** Base Model. ch4/retiarii/common/base\_model.py

import torch

import torch.nn.functional as F

You must use the nni.retiarii.nn.pytorch as nn module to declare layers in a

deep learning model:

import nni.retiarii.nn.pytorch as nn

198

Chapter 4 Multi-trial Neural arChiteCture SearCh

Base Model must be annotated with nni.retiarii.model\_wrapper():

from nni.retiarii import **model\_wrapper**

**@model\_wrapper**

class Net(nn.Module):

Next, we have the classic LeNet model design for the digit recognition problem:

def \_\_init\_\_(self):

super().\_\_init\_\_()

self.conv1 = nn.Conv2d(1, 32, 3, 1)

self.conv2 = nn.Conv2d(32, 64, 3, 1)

self.dropout1 = nn.Dropout(0.25)

self.dropout2 = nn.Dropout(0.5)

self.fc1 = nn.Linear(9216, 128)

self.fc2 = nn.Linear(128, 10)

def forward(self, x):

x = F.relu(self.conv1(x))

x = F.max\_pool2d(self.conv2(x), 2)

x = torch.flatten(self.dropout1(x), 1)

x = self.fc2(self.dropout2(F.relu(self.fc1(x))))

output = F.log\_softmax(x, dim = 1)

return output

Frequent mistakes in Base Model design are:

• Missing @model\_wrapper annotation on Base Model

• Using import torch.nn as nn instead of nni.retiarii.nn.pytorch

as nn declaring layers

**Mutators**

Base Model is a single model. To create Model Space, we have to add Mutators to the Base Model. Each mutator provides a way to change the Base Model. All possible

mutations applied to the Base Model form the Model Space. NNI provides the following mutation operations: LayerChoice, ValueChoice, InputChoice, and Repeat.

199

![](index-213_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

**LayerChoice**

LayerChoice mutator forms the candidate layers for a layer placeholder. One of these layers is tried in the exploration process. LayerChoice mutator is applied to the Base Model the following way:

\# import part

import nni.retiarii.nn.pytorch as nn

\# model design

self.activation = nn.LayerChoice(\[

nn.ReLU(),

nn.Sigmoid(),

nn.Identity

\])

\# forward

x = self.activation(x)

LayerChoice adds layer variations to the Base Model as shown in Figur[e 4-8.](#index_split_001.html#p213)

***Figure 4-8.** LayerChoice Mutator*

LayerChoice is the most straightforward way to mutate the Base Model.

200

Chapter 4 Multi-trial Neural arChiteCture SearCh

**ValueChoice**

ValueChoice forms the list of single values to be tried as layer hyperparameters.

ValueChoice can be used as layer hyperparameters only. It cannot be used as an

arbitrary hyperparameter like batch\_size or learning\_rate in the evaluation process.

ValueChoice mutator is applied to the Base Model the following way:

\# import part

import nni.retiarii.nn.pytorch as nn

\# model design

self.drop = nn.Dropout(nn.ValueChoice(\[0.25, 0.5, 0.75\]))

\# forward

x = self.drop(x)

ValueChoice can be considered as a layer hyperparameter in the HPO context.

**InputChoice**

InputChoice tries different connections. It takes several tensors and chooses n\_chosen tensors from them. InputChoice mutator is applied to the Base Model the following way:

\# import part

import nni.retiarii.nn.pytorch as nn

\# model design

self.switch = nn.InputChoice(n\_candidates = 2, n\_chosen = 1)

\# forward

\# branch one

a = self.op\_a1(x)

a = self.op\_a2(a)

\# branch two

b = self.op\_b1(x)

b = self.op\_b2(b)

\# choosing connection

x = self.switch(\[a, b\])

201

![](index-215_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

InputChoice is designed to find the best data flow branches in neural network

architecture. Figure [4-9](#index_split_001.html#p215) illustrates this concept.

***Figure 4-9.** InputChoice Mutator*

If InputChoice picks more than one candidate tensors (i.e., n\_chosen > 1), then the reduction strategy is applied: sum, mean, concat. This is a very useful technique that allows to extract and merge several connections at the same time. InputChoice for multiple candidates with reduction can be applied the following way:

\# import part

import nni.retiarii.nn.pytorch as nn

\# model design

self.mix = nn.InputChoice(n\_candidates = 3, n\_chosen = 2, reduction = 'sum')

\# forward

\# branch one

a = self.op\_a1(x)

a = self.op\_a2(a)

202

![](index-216_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

\# branch two

b = self.op\_b1(x)

b = self.op\_b2(b)

\# branch three

c = self.op\_b1(x)

c = self.op\_b2(c)

\# choosing connection

x = self.mix(\[a, b, c\])

The preceding code generates the search space shown in Figure [4-10](#index_split_001.html#p216).

***Figure 4-10.** InputChoice Mutator for multiple candidates*

InputChoice Mutator for multiple candidates can choose the same tensor several

times. It happens when other connections do not bring any helpful information to neural network performance.

203

Chapter 4 Multi-trial Neural arChiteCture SearCh

Also, InputChoice allows adding skip connection technique to neural architecture.

Skip connection is one of the core techniques in modern neural network design. It was first introduced in 2015 in “Deep Residual Learning for Image Recog[nition” (https://](https://arxiv.org/pdf/1512.03385.pdf)

[arxiv.org/pdf/1512.03385.pdf](https://arxiv.org/pdf/1512.03385.pdf)). Skip connection can be implemented using the following pattern:

\# import part

import nni.retiarii.nn.pytorch as nn

\# model design

self.skip\_connect = nn.InputChoice(n\_candidates = 2, n\_chosen = 1)

\# forward

x0 = x.clone()

\# connection

x1 = self.op(x)

x0 = self.skip\_connect(\[x0, None\])

if x0 is not None:

\# skipping connection

x1 += x0

In the first case, the model will use the skip connection technique, but not in the second one. Figur[e 4-11 demons](#index_split_002.html#p218)trates skip connection mutation.

204

![](index-218_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-11.** InputChoice. Skip connection mutation*

Let’s examine the application of the InputChoice mutator using an arithmetic

DFG as an example. Say we have *x* = 1 and three operator pipelines which consist of multiplication operators:

1: *x* → ( *x* × 2)

2: x → (x × 2) → (x × 3)

3: x → (x × 2) → (x × 3) → (x × 4)

You need to select two pipelines whose sum is maximum. You can select the same

pipeline twice. This is a fairly simple task. It is intuitively clear that the sum of the last pipeline will give the maximum value. Let’s run the third pipeline: 1 → 1 × 2 → 2 × 3 → 6

× 4 → 24; thus, the maximum value we can obtain is 48.

Now let’s obtain the same result using NNI and InputChoice Mutator

using Listing [4-4](#index_split_002.html#p219).

205

Chapter 4 Multi-trial Neural arChiteCture SearCh

Importing common modules:

***Listing 4-4.*** InputChoice Model Space. ch4/retiarii/common/input\_choice/

model\_space.py

import os

import torch

Importing nni modules:

import nni

import nni.retiarii.nn.pytorch as nn

from nni.retiarii import model\_wrapper

ProdBlock acts as a multiplier operator. It simply multiplies the tensor by

some value:

class ProdBlock(nn.Module):

def \_\_init\_\_(self, multiplier = 0):

super().\_\_init\_\_()

self.multiplier = multiplier

def forward(self, x):

x = x \* self.multiplier

return x

Next, we define the Model Space:

@model\_wrapper

class InputChoiceModelSpace(nn.Module):

def \_\_init\_\_(self):

super().\_\_init\_\_()

We declare multiplier operators

self.x2 = ProdBlock(2)

self.x3 = ProdBlock(3)

self.x4 = ProdBlock(4)

206

Chapter 4 Multi-trial Neural arChiteCture SearCh

and InputChoice mutator that will select the best pair of pipelines:

self.mix = nn.InputChoice(

n\_candidates = 3,

n\_chosen = 2,

reduction = 'sum'

)

forward action executes three different pipelines, and InputChoice mutator tries only two of them:

def forward(self, x):

First pipeline: x → (x × 2)

\# Branch A

a = self.x2(x)

Second pipeline: 2: x → (x × 2) → (x × 3)

\# Branch B

b = self.x2(x)

b = self.x3(b)

Third pipeline: x → (x × 2) → (x × 3) → (x × 4)

\# Branch C

c = self.x2(x)

c = self.x3(c)

c = self.x4(c)

return self.mix(\[a, b, c\])

Here is the evaluation function:

def evaluate(model\_cls):

model = model\_cls()

x = 1

out = model(x)

207

![](index-221_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

\# visualizing

onnx\_dir = os.path.abspath(os.environ.get('NNI\_OUTPUT\_DIR', '.'))

os.makedirs(onnx\_dir, exist\_ok = True)

torch.onnx.export(model, x, onnx\_dir + '/model.onnx')

nni.report\_final\_result(out)

Now we can run the experiment using this script:

$ python3 ch4/retiarii/common/input\_choice/run\_experiment.py

You can analyze the results on the WebUI detail pag[e: http://127.0.0.1:8080/detail.](http://127.0.0.1:8080/detail)

***Figure 4-12.** InputChoice Experiment results*

In Figur[e 4-12](#index_split_002.html#p221), we see 32 = 9 trials. The best trial shows 48 and has the following parameters: { "model\_1\_0": 2, "model\_1\_1": 2 }, which means that the best result is achieved with the last pipelines.

return self.mix(

\[

a, # <- 0

b, # <- 1

c # <- 2

\])

Such simple examples help to understand better how mutators act before

proceeding to a real NAS.

208

![](index-222_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

**Repeat**

Repeat mutator repeats some action a certain number of times. In the NAS context, the Repeat mutator tries to determine how often to iterate the same neural network block.

For example, the ResNet neural network architecture implies a stack of Residual Blocks.

But the optimal number of Residual Blocks may depend on the specific task. Figure [4-13](#index_split_002.html#p222)

shows part of the ResNet architecture.

***Figure 4-13.** ResNet architecture*

209

Chapter 4 Multi-trial Neural arChiteCture SearCh

Repeat mutator accepts a function that generates a block by its sequence number.

Here is the pattern how Repeat mutator can be applied:

import nni.retiarii.nn.pytorch as nn

from nni.retiarii import model\_wrapper

We define a custom model block:

class SomeBlock(nn.Module):

...

Set a builder function that generates a block concerning its ordinal number in

the stack:

def create\_some\_block(block\_num):

\# some logic here that depends on 'block\_num'

return SomeBlock(block\_num)

@model\_wrapper

class RepeatModelSpace(nn.Module):

def \_\_init\_\_(self):

super().\_\_init\_\_()

...

Defining Repeat mutator:

self.repeat\_block = nn.Repeat(

create\_some\_block,

depth = (1, 5) # repeat from 1 to 5 times

)

...

def forward(self, x):

...

Evaluating Repeat mutator:

x = self.repeat\_block(x)

...

210

Chapter 4 Multi-trial Neural arChiteCture SearCh

Therefore, it would be handy to have a tool that iteratively constructs block

stacks of various lengths. And that’s what the Repeat Mutator does. Let’s examine the implementation of the Repeat mutator for a synthetic arithmetic task, as we did for the InputChoice mutator. Say we have a sequence of blocks that add values to a tensor. And we need to find the optimal length of this sequence. Listing [4-5](#index_split_002.html#p224) describes the Model Space for this problem.

AddBlock acts as an addition operator. It simply adds some value to the input tensor.

***Listing 4-5.*** Repeat Mutator Model Space. ch4/retiarii/common/repeat/model\_

space.py

class AddBlock(nn.Module):

def \_\_init\_\_(self, add = 0):

super().\_\_init\_\_()

self.add = add

def forward(self, x):

x = x + self.add

return x

Builder function that creates AddBlock by its ordinal number:

@classmethod

def create(cls, block\_num):

return AddBlock(block\_num)

Next, we define the Model Space:

@model\_wrapper

class RepeatModelSpace(nn.Module):

def \_\_init\_\_(self):

super().\_\_init\_\_()

211

Chapter 4 Multi-trial Neural arChiteCture SearCh

Repeat mutator generates block sequences of different lengths (from 1 to 5):

self.repeat = nn.Repeat(

AddBlock.create,

depth = (1, 5)

)

def forward(self, x):

return self.repeat(x)

You can examine the experiment by running

$ python3 ch4/retiarii/common/repeat/run\_experiment.py

In fact, the primitive mutators LayerChoice, ValueChoice, InputChoice, and Repeat allow you to construct a space of any complexity. These mutators can be compared to programming language directives:

• *set*: LayerChoice, ValueChoice

• *if*: InputChoice

• *loop*: Repeat

Later in this chapter, we will examine a Model Space construction for a real NAS task using these mutators.

**Labeling**

All the mutator APIs have an optional argument label. Mutators with the same label will share the same value. A typical example is

self.net = nn.Sequential(

nn.Linear(10, nn.ValueChoice(\[32, 64, 128\], label='hidden\_dim'),

nn.Linear(nn.ValueChoice(\[32, 64, 128\], label='hidden\_dim'), 3)

)

212

Chapter 4 Multi-trial Neural arChiteCture SearCh

which is the same as

hidden\_dim = nn.ValueChoice(\[32, 64, 128\], label='hidden\_dim')

self.net = nn.Sequential(

nn.Linear(10, hidden\_dim,

nn.Linear(hidden\_dim, 3)

)

**Example**

Listin[g 4-6 demons](#index_split_002.html#p226)trates a trivial example of the Model Space applied to the image classification network.

***Listing 4-6.*** Model Space. ch4/retiarii/common/model\_space.py

@model\_wrapper

class Net(nn.Module):

def \_\_init\_\_(self):

super().\_\_init\_\_()

self.conv1 = nn.Conv2d(1, 32, 3, 1)

Applying LayerChoice mutator:

self.conv2 = nn.LayerChoice(\[

nn.Conv2d(32, 64, 3, 1),

nn.Identity

\], label = 'conv\_layer')

Applying ValueChoice mutator as Dropout layer hyperparameter value:

self.dropout1 = nn.Dropout(

nn.ValueChoice(\[0.25, 0.5, 0.75\]),

label = 'dropout'

)

self.dropout2 = nn.Dropout(0.5)

213

Chapter 4 Multi-trial Neural arChiteCture SearCh

Applying ValueChoice mutator as Linear hyperparameter value:

feature = nn.ValueChoice(

\[64, 128, 256\],

label = 'hidden\_size'

)

self.fc1 = nn.Linear(9216, feature)

self.fc2 = nn.Linear(feature, 10)

def forward(self, x):

x = F.relu(self.conv1(x))

x = F.max\_pool2d(self.conv2(x), 2)

x = torch.flatten(self.dropout1(x), 1)

x = self.fc2(self.dropout2(F.relu(self.fc1(x))))

output = F.log\_softmax(x, dim = 1)

return output

**Evaluators**

Retiarii Evaluator is a function that accepts a model class, initiates a model, trains it, tests it, and returns a result to Experiment. Evaluator can be implemented using the following pattern:

def evaluate(model\_cls):

\# Initiate model

model = model\_cls()

\# Saving model graph for Visualization

onnx\_dir = os.path.abspath(os.environ.get('NNI\_OUTPUT\_DIR', '.'))

os.makedirs(onnx\_dir, exist\_ok = True)

torch.onnx.export(model, input\_x, onnx\_dir + '/model.onnx')

\# Model Training

\# ... passing intermediate results

\# ... nni.report\_intermediate\_result()

\# Model Testing

\# nni.report\_final\_result(out)

214

Chapter 4 Multi-trial Neural arChiteCture SearCh

Retiarii Evaluator is pretty close to the Trial approach we used in HPO in previous chapters.

**Exploration Strategies**

NNI provides the following exploration strategies for Multi-shot NAS: *Random* *Strategy*, *Grid Search*, *Regularized Evolution*, *TPE Strategy*, and *RL Strategy*. We are already familiar with some of them because they implement the same approach as

corresponding HPO Tuners. But anyway, let’s briefly study each of them.

**Random Strategy**

Random Strategy (nni.retiarii.strategy.Random) randomly samples new models

from the Model Space. It is a simple but still effective technique to Explore Model Space.

Random Search is a good first-time Exploration Strategy, and it can give you good clues when you have no idea about the dataset you are dealing with and suitable architecture designs. Usually, Random Search is used first, and after the Model Space is refined, a more intelligent Exploration Strategy is applied.

**Grid Search**

Grid Search Strategy (nni.retiarii.strategy.GridSearch) samples new models from

Model Space using a Grid Search algorithm.

**Regularized Evolution**

Regularized Evolution Strategy (nni.retiarii.strategy.RegularizedEvolution)

implements Genetic Algorithm Search with mutation operator using Tournament Selection method. Regularized Evolution Strategy is close to Evolution Tuner we studied in Chapter [3](https://doi.org/10.1007/978-1-4842-8149-9_3).

Pseudo-code that describes Regularized Evolution Algorithm is provided in the following.

Regularized Evolution Strategy has three global hyperparameters:

• POPULATION\_SIZE: The size of a population that will try to participate

in evolution search

• CANDIDATES\_N: Number of candidates Tournament Selection method

will pick from the population

• GENERATION\_N: Total number of cycles

215

Chapter 4 Multi-trial Neural arChiteCture SearCh

\# HYPERPARAMETERS

POPULATION\_SIZE

CANDIDATES\_N

GENERATIONS\_N

The population is initialized with random individuals (i.e., random neural

architecture):

population = \[\]

for \_ in range(POPULATION\_SIZE):

individual = generate\_random\_architecture()

evaluate(individual)

population.append(individual)

for \_ in range(GENERATIONS):

Algorithm picks CANDIDATES\_N random individuals from population:

candidates = random\_choice(population, CANDIDATES\_N)

From these candidates, the best one is selected (i.e., the individual that has the best metric):

best\_candidate = get\_best\_from(candidates)

Random mutation is performed on the best candidate (i.e., algorithm runs several Mutators in the original model):

mutant = mutate(best\_candidate)

Mutant individual is being evaluated:

evaluate(mutant)

Mutant replaces the worst individual in the population:

replace\_worst(population, mutant)

Figur[e 4-14 demons](#index_split_002.html#p230)trates the algorithm of Regularized Evolution Strategy.

216

![](index-230_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-14.** Regularized Evolution Strategy*

The implementation of Regularized Evolution Strategy has the following parameters:

• optimize\_mode:

**Type**: string

**Default**: maximize

**Values**: ’maximize’ | ’minimize’

Sets the evolution direction.

• population\_size:

**Type:** int

**Default:** 100

The number of individuals in the population.

• cycles:

**Type**: int

**Default**: 20000

The number of generations of the algorithm.

• sample\_size:

**Type**: int

**Default**: 25

The number of individuals that should participate in each

Tournament Selection.

217

Chapter 4 Multi-trial Neural arChiteCture SearCh

• mutation\_prob:

**Type**: float

**Default**: 0.05

Probability that mutation occurs in each mutator in the Model Space.

For more details, please refer to the original paper describing Regularized Evolution approach[: https://arxiv.org/abs/1802.01548](https://arxiv.org/abs/1802.01548).

**TPE Strategy**

TPE Strategy (nni.retiarii.strategy.TPEStrategy) is a Sequential Model-Based

Optimization approach based on Tree-structured Parzen Estimator. It acts the same way as TPE Tuner we studied in Chapter [3.](https://doi.org/10.1007/978-1-4842-8149-9_3)

For more details, please refer to the original paper describing the TPE approach:

[https://papers.nips.cc/paper/2011/file/86e8f7ab32cfd12577bc2619bc635690-](https://papers.nips.cc/paper/2011/file/86e8f7ab32cfd12577bc2619bc635690-Paper.pdf)

[Paper.pdf](https://papers.nips.cc/paper/2011/file/86e8f7ab32cfd12577bc2619bc635690-Paper.pdf).

**RL Strategy**

RL Strategy (nni.retiarii.strategy.PolicyBasedRL) implements the Reinforcement

Learning approach based on policy-gradient method (Proximal Policy Optimization or PPO). RL Strategy implements a special Recurrent Neural Network called Controller.

Controller generates various model architectures from Model Space. The Controller acts as a stochastic policy; hence, it returns the mutation probability for each of the Mutators in the Model Space. After each trial, the Controller updates the weights of its RNN

according to the Proximal Optimization Policy method. This approach allows exploring the Model Space by constructing a probability distribution for each of the mutators.

Figur[e 4-15 demons](#index_split_002.html#p232)trates RL Strategy in action.

218

![](index-232_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-15.** Reinforcement Learning (Proximal Policy Optimization) Strategy* RL Strategy requires tianshou package to be installed. Tianshou is a Reinforcement Learning platform based on pure PyTorch.

pip install tianshou

The implementation of RL Strategy has the following parameters:

• max\_collect:

**Type**: int

**Default**: 100

How many epochs Exploration Strategy performs.

219

Chapter 4 Multi-trial Neural arChiteCture SearCh

• Trial\_per\_collect:

**Type**: int

**Default**: 20

How many trials (trajectories) each time collector collects. After each completed trajectory, the trainer will sample the batch from the replay buffer and do the

Controller update.

For more details, please refer to the original paper describing the Neural Architecture Search with Reinforcement Learning: [https://arxiv.org/pdf/1611.01578.pdf.](https://arxiv.org/pdf/1611.01578.pdf)

**Experiment**

And the last thing left is the Experiment. Retiarii Experiment is launched in stand-alone (embedded) mode and contains seven steps:

• Declare Model Space

• Declare Model Evaluator

• Declare Exploration Strategy

• Initialize Retiarii Experiment

• Configure Retiarii Experiment

• Launch Experiment

• Returning results

The following pattern can be used to create Retiarii Experiment:

import nni.retiarii.strategy as strategy

from nni.retiarii import model\_wrapper

from nni.retiarii.evaluator import FunctionalEvaluator

from nni.retiarii.experiment.pytorch import RetiariiExeConfig,

RetiariiExperiment,

\# Declare Model Space

base\_model = Net()

\# Declare Model Evaluator

search\_strategy = strategy.Random()

220

Chapter 4 Multi-trial Neural arChiteCture SearCh

\# Declare Exploration Strategy

model\_evaluator = FunctionalEvaluator(evaluate\_model)

\# Initialize Retiarii Experiment

exp = RetiariiExperiment(base\_model, model\_evaluator, \[\], search\_strategy)

\# Configure Retiarii Experiment

exp\_config = RetiariiExeConfig('local')

exp\_config.experiment\_name = 'mnist\_search'

exp\_config.trial\_concurrency = 2

exp\_config.max\_trial\_number = 20

exp\_config.training\_service.use\_active\_gpu = False

export\_formatter = 'dict'

\# uncomment this for graph-based execution engine

\# exp\_config.execution\_engine = 'base'

\# export\_formatter = 'code'

\# Launch Experiment

exp.run(exp\_config, 8081 + random.randint(0, 100))

\# Returning results

print('Final model:')

for model\_code in exp.export\_top\_models(formatter=export\_formatter):

print(model\_code)

You can use the WebUI after running the experiment the same way we did earlier

launching HPO experiments.

**CIFAR-10 LeNet NAS**

Let’s study the application of Multi-trial NAS to the CIFAR-10 problem. CIFAR-10 is a common dataset for image classification problem. It contains 60,000 color images (32×32

pixels) from 10 different classes: *airplane*, *automobile*, *bird*, *cat*, *deer*, *dog*, *frog*, *horse*, *ship*, and *truck*.

Please run the following command to download the CIFAR-10 dataset to your

machine:

$ python3 ch4/utils/datasets.py

221

![](index-235_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

Figur[e 4-16 demons](#index_split_002.html#p235)trates several samples from CIFAR10 dataset.

***Figure 4-16.** CIFAR-10 samples*

Let’s try to find an appropriate deep learning model based on the LeNet approach solving the CIFAR-10 classification problem. As we already know, the LeNet image recognition architecture can be divided into two components: *Feature Extraction* *Component* and *Decision Maker Component*. The *Feature Extraction Component* consists of a sequence of Feature Extraction blocks with convolution layer. *Decision Maker* *Component* consists of Fully Connected Components with linear layer.

The design of the Feature Extraction block can be as follows:

• Conv → Activation

• Conv → Pool → Activation

Figur[e 4-17 demons](#index_split_002.html#p236)trates possible architecture options for the Feature Extraction block or Feature Extraction block space.

222

![](index-236_1.png)

![](index-236_2.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-17.** Feature Extraction block space*

In the same way, we can determine the possible designs for the Fully

Connected block:

• Linear → Activation

• Linear → Dropout → Activation

Figur[e 4-18 illus](#index_split_002.html#p236)trates Fully Connected block space.

***Figure 4-18.** Fully Connected block space*

**Note** actually,

Linear → Dropout(p=1) → Activation equals Linear →

Activation, and it is possible to design the same block space from Figure [4-18](#index_split_002.html#p236)

without using two connections. We could achieve the same block space using

simple layer hyperparameter Optimization: Linear → Dropout(p=\[.3, .5,

.8, 1\]) → Activation. But we use two connections on purpose here because

we want to demonstrate how the Multi-trial NaS chooses the best connection.

223

![](index-237_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

The neural architecture we are looking for consists of Feature Extraction and Fully Connected block sequences. Each of these blocks may have the architecture shown in Figures [4-17 and 4-18](#index_split_002.html#p236), respectively. The LeNet NAS algorithm must find the optimal Feature Extraction and Fully Connected block sequence lengths, as well as their

architectures. The Model Space for LeNet NAS can be drawn as depicted in Figure [4-19.](#index_split_002.html#p237)

***Figure 4-19.** LeNet NAS Model Space*

We will start implementing the CIFAR-10 LeNet NAS by defining a Feature Extraction block in Listing [4-7](#index_split_002.html#p237).

***Listing 4-7.*** Feature Extraction block. ch4/retiarii/cifar\_10\_lenet/feature\_

extraction.py

from typing import Tuple

import nni.retiarii.nn.pytorch as nn

224

Chapter 4 Multi-trial Neural arChiteCture SearCh

FeatureExtractionBlock takes the following parameters:

• dim: Input–output channels

• kernel\_size: Kernel of convolution layer

• activation: Activation function

• block\_num: Ordinal number of the block in Feature Extraction

sequence

class FeatureExtractionBlock(nn.Module):

def \_\_init\_\_(

self,

dim: Tuple\[int, int\],

kernel\_size,

activation,

block\_num = 0

) -> None:

super().\_\_init\_\_()

Initializing core convolution layer:

self.input\_dim = dim\[0\]

self.output\_dim = dim\[1\]

self.conv = nn.Conv2d(

in\_channels = self.input\_dim,

out\_channels = self.output\_dim,

kernel\_size = kernel\_size

)

Declaring pool and activation layers:

self.max\_pool = nn.MaxPool2d(2, 2)

self.activation = activation

225

Chapter 4 Multi-trial Neural arChiteCture SearCh

Switch choice for two different branches:

• Conv → Pool → Activation

• Conv → Activation

self.switch = nn.InputChoice(

n\_candidates = 2,

n\_chosen = 1,

label = f'fe\_switch\_{block\_num}'

)

Defining forward method:

def forward(self, x):

x = self.conv(x)

\# Branch A

a = self.max\_pool(x)

a = self.activation(a)

\# Branch B

b = self.activation(x)

return self.switch(\[a, b\])

The following method is used in Repeat Mutator. It returns an appropriate

FeatureExtractionBlock by its ordinal number in the Feature Extraction sequence.

@classmethod

def create(cls, activation, in\_dimension):

def create\_block(i):

params = {

'kernel\_size': nn.ValueChoice(

\[3, 5\],

label = f'fe\_kernel\_size\_{i}'

)

}

226

Chapter 4 Multi-trial Neural arChiteCture SearCh

\# Feature Block Dimensions

if i == 0:

dim = (in\_dimension, 8)

elif i == 1:

dim = (8, 16)

else:

dim = (16, 16)

params\['dim'\] = dim

params\['activation'\] = activation

return FeatureExtractionBlock(\*\*params)

return create\_block

Fully Connected block implementation is similar to Feature Extraction Block and is provided in Listin[g 4-8.](#index_split_002.html#p240)

***Listing 4-8.*** Fully Connected block. ch4/retiarii/cifar\_10\_lenet/fully\_

connected.py

from typing import Tuple, Iterator

from torch.nn import Parameter

import nni.retiarii.nn.pytorch as nn

FullyConnectedBlock takes the following parameters:

• dim: Input–output features for linear layer

• dropout\_rate: Layer hyperparameter for dropout layer

• activation: Activation function

• block\_num: Ordinal number of the block in Fully Connected

sequence

class FullyConnectedBlock(nn.Module):

def \_\_init\_\_(

self,

dim: Tuple\[int, int\],

227

Chapter 4 Multi-trial Neural arChiteCture SearCh

dropout\_rate,

activation,

block\_num

) -> None:

super().\_\_init\_\_()

Initializing linear layer:

self.input\_dim = dim\[0\]

self.output\_dim = dim\[1\]

self.\_linear = None

Declaring dropout and activation layers:

self.dropout = nn.Dropout(p = dropout\_rate)

self.activation = activation

Switch choice for two different branches:

• Linear → Dropout → Activation

• Linear → Activation

self.switch = nn.InputChoice(

n\_candidates = 2,

n\_chosen = 1,

label = f'fc\_switch\_{block\_num}'

)

Defining forward method:

def forward(self, x):

if not self.input\_dim:

self.input\_dim = x.shape\[1\]

\# Branch A

a = self.linear(x)

a = self.dropout(a)

a = self.activation(a)

228

Chapter 4 Multi-trial Neural arChiteCture SearCh

\# Branch B

b = self.linear(x)

b = self.activation(b)

return self.switch(\[a, b\])

The following method is used in Repeat Mutator. It returns an appropriate

FullyConnectedBlock by its ordinal number in the Fully Connected sequence.

@classmethod

def create(cls, activation, units, dropout\_rate):

def create\_block(i):

return FullyConnectedBlock(

dim = (units\[i\], units\[i + 1\]),

dropout\_rate = dropout\_rate,

activation = activation,

block\_num = i

)

return create\_block

And now we are ready to build LeNet Model Space.

Importing modules:

***Listing 4-9.*** LeNet Model Space. ch4/retiarii/cifar\_10\_lenet/lenet\_model\_

space.py

from typing import Iterator

from torch.nn import Parameter

import nni.retiarii.nn.pytorch as nn

from nni.retiarii import model\_wrapper

from ch4.retiarii.cifar\_10\_lenet.feature\_extraction import

FeatureExtractionBlock

from ch4.retiarii.cifar\_10\_lenet.fully\_connected import FullyConnectedBlock

229

Chapter 4 Multi-trial Neural arChiteCture SearCh

Do not forget to add @model\_wrapper to the Model Space class:

@model\_wrapper

class Cifar10LeNetModelSpace(nn.Module):

def \_\_init\_\_(self):

super().\_\_init\_\_()

\# number of classes for CIFAR-10 dataset

self.class\_num = 10

\# RGB input channels

self.input\_channels = 3

First, we define the space for the Feature Extraction sequence. All Feature Extraction blocks will share the same activation function:

fe\_activation = nn.LayerChoice(

\[nn.Sigmoid(), nn.ReLU()\],

label = f'fe\_activation'

)

Repeat mutator will create two or three Feature Extraction blocks in a row:

self.fe = nn.Repeat(

FeatureExtractionBlock.create(fe\_activation, self.input\_channels),

depth = (2, 3), label = 'fe\_repeat'

)

Second, we define a Fully Connected sequence:

self.flat = nn.Flatten()

All Fully Connected blocks will share the same activation function:

dm\_activation = nn.LayerChoice(

\[nn.Sigmoid(), nn.ReLU()\],

label = f'fc\_activation'

)

230

Chapter 4 Multi-trial Neural arChiteCture SearCh

Layer hyperparameters for Fully Connected blocks:

l1\_size = nn.ValueChoice(\[256, 128\], label = 'l1\_size')

l2\_size = nn.ValueChoice(\[128, 64\], label = 'l2\_size')

l3\_size = nn.ValueChoice(\[64, 32\], label = 'l3\_size')

dropout\_rate = nn.ValueChoice(\[.3, .5\], label = 'fc\_dropout\_rate')

Repeat mutator will create from one to three Fully Connected blocks in a row:

self.dm = nn.Repeat(

FullyConnectedBlock.create(

dm\_activation,

\[None, l1\_size, l2\_size, l3\_size\],

dropout\_rate

),

depth = (1, 3), label = 'fc\_repeat'

)

Final pair of classification layers (linear\_final layer initialized lazily):

self.linear\_final\_input\_dim = None

self.\_linear\_final = None

self.log\_max = nn.LogSoftmax(dim = 1)

Executing forward method:

def forward(self, x):

x = self.fe(x)

x = self.flat(x)

x = self.dm(x)

if not self.linear\_final\_input\_dim:

self.linear\_final\_input\_dim = x.shape\[1\]

x = self.linear\_final(x)

return self.log\_max(x)

Model evaluator is a classical neural network train–test algorithm. You can examine its code here: ch4/retiarii/cifar\_10\_lenet/eval.py.

Fine! Since LeNet Model Space is ready, we can start the research with the code in Listin[g 4-10.](#index_split_002.html#p245)

231

Chapter 4 Multi-trial Neural arChiteCture SearCh

Importing modules:

***Listing 4-10.*** LeNet NAS Experiment. ch4/retiarii/cifar\_10\_lenet/run\_cifar10\_

lenet\_experiment.py

from nni.retiarii.evaluator import FunctionalEvaluator

from nni.retiarii.experiment.pytorch import RetiariiExperiment,

RetiariiExeConfig

import nni.retiarii.strategy as strategy

from ch4.retiarii.cifar\_10\_lenet.eval import evaluate

from ch4.retiarii.cifar\_10\_lenet.lenet\_model\_space import

Cifar10LeNetModelSpace

Declaring Model Space:

model\_space = Cifar10LeNetModelSpace()

Defining Model Evaluator:

evaluator = FunctionalEvaluator(evaluate)

We will use RL Search Strategy for this experiment:

search\_strategy = strategy.PolicyBasedRL(

trial\_per\_collect = 10,

max\_collect = 200

)

Initializing Retiarii Experiment:

exp = RetiariiExperiment(model\_space, evaluator, \[\], search\_strategy)

Experiment configuration:

exp\_config = RetiariiExeConfig('local')

exp\_config.experiment\_name = 'CIFAR10\_LeNet\_NAS'

exp\_config.trial\_concurrency = 1

exp\_config.max\_trial\_number = 500

exp\_config.training\_service.use\_active\_gpu = False

export\_formatter = 'dict'

232

Chapter 4 Multi-trial Neural arChiteCture SearCh

Launching Experiment:

exp.run(exp\_config, 8080)

Returning results:

print('Final model:')

for model\_code in exp.export\_top\_models(formatter = export\_formatter):

print(model\_code)

The experiment can be run as follows:

$ python3 ch4/retiarii/cifar\_10\_lenet/run\_cifar10\_lenet\_experiment.py

**Note** Duration ~ 20 hours on intel Core i7 with CuDa (GeForce GtX 1050)

The best model shows **0.84** accuracy on test dataset. It is not a bad result, but it seems there is still room for improvement. The best model has the following parameters:

{

"fe\_repeat": 2,

"fe\_kernel\_size\_0": 3,

"fe\_activation": "1",

"fe\_switch\_0": 0,

"fe\_kernel\_size\_1": 5,

"fe\_kernel\_size\_2": 3,

"fc\_repeat": 2,

"l1\_size": 128,

"fc\_dropout\_rate": 0.3,

"fc\_switch\_0": 0,

"l2\_size": 64,

"fc\_switch\_1": 0,

"l3\_size": 64,

"fc\_switch\_2": 0

}

233

Chapter 4 Multi-trial Neural arChiteCture SearCh

The preceding parameters can be interpreted the following way:

"fe\_repeat": 2 – means that Repeat mutator generates the Feature Extraction sequence of two blocks:

self.fe = nn.Sequential(

\[

FeatureExtractionBlock.create(fe\_activation, self.input\_

channels)(0),

FeatureExtractionBlock.create(fe\_activation, self.input\_

channels)(1),

\]

)

"fe\_kernel\_size\_0": 3 – means that 3 is chosen in ValueChoice mutator:

'kernel\_size': nn.ValueChoice(

\[3, # <- this value

5\],

label = f'fe\_kernel\_size\_{i}'

)

"fe\_switch\_0": 0 – means that the first connection is used in InputChoice mutator: self.switch(\[a, b\]) <- returns a

Also, it is convenient to visualize the architecture using Netron in Trial details panel.

Figur[e 4-20 demons](#index_split_002.html#p248)trates the architecture of the best model.

234

![](index-248_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-20.** LeNet NAS Best Model Architecture*

235

![](index-249_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

The research we made in this section can be a good starting point for your own NAS

solutions. It contains basic techniques used in Multi-trial NAS. Here, we used the LeNet model as the Base Model, but you can choose any model and any mutators that fit the concrete problem better. But we haven’t achieved a great result in the LeNet NAS. In the next section, we’ll try another NAS with a more sophisticated approach.

**CIFAR-10 ResNet NAS**

Let’s try to find another approach to the architecture search that solves the CIFAR-10

problem. In 2015, the article “Deep Residual Learning for Image Recog[nition” (https://](https://arxiv.org/pdf/1512.03385.pdf)

[arxiv.org/pdf/1512.03385.pdf](https://arxiv.org/pdf/1512.03385.pdf)) was published. This article had a huge impact on deep learning in general. It introduced the concept of a residual term, which could degrade the blocks of the neural network, which overwhelmed its performance.

The basic building block of the ResNet model is the Bottleneck block. Original

Bottleneck block skips connections inside. But we will add this as an optional feature.

NAS algorithm will define if it is appropriate to use the skip connection technique for the Bottleneck block. So there are two variants of Bottleneck block in ResNet NAS *with* and *without* skip connection technique. The architecture of the Bottleneck block space can be demonstrated as shown in Figur[e 4-21](#index_split_002.html#p249).

***Figure 4-21.** Bottleneck block space*

236

![](index-250_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

Another component of ResNet is the Residual Cell. Residual Cell consists of

a sequence of Bottleneck blocks. The optimal length of the Bottleneck sequence

in Residual Cell depends on the concrete dataset. Figur[e 4-22 sho](#index_split_002.html#p250)ws the Residual Cell space.

***Figure 4-22.** Residual Cell space*

And finally, we can construct the ResNet model. ResNet has the following

architecture:

• Initial convolution layer

• Residual Cell sequence

• Several Fully Connected layers

The optimal length of a Residual Cell sequence depends on the dataset. And we

will try to find it in ResNet NAS. Figure [4-23](#index_split_002.html#p251) presents the complete Model Space for ResNet NAS.

237

![](index-251_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-23.** ResNet NAS space*

Listin[g 4-11 defines the B](#index_split_002.html#p251)ottleneck block for ResNet Model Space.

***Listing 4-11.*** ResNet NAS Bottleneck block. ch4/retiarii/cifar\_10\_resnet/

bottle\_neck.py

import nni.retiarii.nn.pytorch as nn

class Bottleneck(nn.Module):

Bottleneck expansion ratio:

expansion = 4

The number of output channels that are produced by Bottleneck block:

@classmethod

def result\_channels\_num(cls, channels):

return channels \* cls.expansion

Bottleneck takes the following parameters:

• cell\_num: The ordinal number of Residual Cell this block belongs to

• in\_channels: Input channels to the first convolution layer

238

Chapter 4 Multi-trial Neural arChiteCture SearCh

• out\_channels: Output channels to all convolutional layers in

the block

• i\_downsample: Identity downsample block

def \_\_init\_\_(

self,

cell\_num,

in\_channels,

out\_channels,

i\_downsample = None,

stride = 1

):

super(Bottleneck, self).\_\_init\_\_()

Defining three convolution layers with batch normalization:

self.conv1 = nn.Conv2d(

in\_channels, out\_channels,

kernel\_size = 1, stride = 1, padding = 0

)

self.batch\_norm1 = nn.BatchNorm2d(out\_channels)

self.conv2 = nn.Conv2d(

out\_channels, out\_channels,

kernel\_size = 3, stride = stride, padding = 1

)

self.batch\_norm2 = nn.BatchNorm2d(out\_channels)

self.conv3 = nn.Conv2d(

out\_channels, self.result\_channels\_num(out\_channels),

kernel\_size = 1, stride = 1, padding = 0

)

self.batch\_norm3 = nn.BatchNorm2d(self.result\_channels\_num(out\_

channels))

239

Chapter 4 Multi-trial Neural arChiteCture SearCh

Skip connection acts the same for all blocks in Residual Cell because all InputChoice mutators share the same label in the Residual Cell:

self.skip\_connection = nn.InputChoice(

n\_candidates = 2,

n\_chosen = 1,

label = f'bottle\_neck\_{cell\_num}\_skip\_connection'

)

Identity downsampling block:

self.i\_downsample = i\_downsample

self.stride = stride

self.relu = nn.ReLU()

Defining forward method:

def forward(self, x):

\# x0

identity = x.clone()

x = self.relu(self.batch\_norm1(self.conv1(x)))

x = self.relu(self.batch\_norm2(self.conv2(x)))

x = self.conv3(x)

x = self.batch\_norm3(x)

identity = self.skip\_connection(\[identity, None\])

Skipping connection if self.skip\_connection returns not None:

if identity is not None:

#downsample if needed

if self.i\_downsample is not None:

identity = self.i\_downsample(identity)

\# adding identity

x += identity

240

Chapter 4 Multi-trial Neural arChiteCture SearCh

x = self.relu(x)

return x

Since we have defined the Bottleneck block, we can move to the ResNet Model Space definition in Listin[g 4-12.](#index_split_002.html#p254)

(Some unimportant code segments are omitted. Complete code is provided in the

corresponding file: *ch4/retiarii/cifar\_10\_resnet/res\_net\_model\_space.py*.) Importing modules:

***Listing 4-12.*** ResNet NAS Model Space

from typing import Iterator

import nni.retiarii.nn.pytorch as nn

from nni.retiarii import model\_wrapper

from torch.nn import Parameter

from ch4.retiarii.cifar\_10\_resnet.bottle\_neck import Bottleneck

Don’t forget to annotate Model Space with @model\_wrapper:

@model\_wrapper

class ResNetModelSpace(nn.Module):

Global model constants:

\# classification classes

num\_classes = 10

\# input channels for RGB image

in\_channels = 3

\# ResNet Channel constant

channels = 64

def \_\_init\_\_(self):

super().\_\_init\_\_()

Choosing ReLU as a global activation function:

self.relu = nn.ReLU()

241

Chapter 4 Multi-trial Neural arChiteCture SearCh

Entry point convolution layer with batch normalization:

self.conv1 = nn.Conv2d(

in\_channels = self.in\_channels,

out\_channels = self.channels,

kernel\_size = 7,

stride = 2,

padding = 3,

bias = False

)

self.batch\_norm1 = nn.BatchNorm2d(64)

MaxPool layer with the following hyperparameter list \[2, 3\]:

pool\_size = nn.ValueChoice(\[2, 3\], label = 'pool\_size')

self.max\_pool = nn.MaxPool2d(kernel\_size = pool\_size, stride = 2,

padding = 1)

Constructing Residual Cell sequence with Repeat mutator (from two to five cells): self.res\_cells = nn.Repeat(

ResNetModelSpace.residual\_cell\_builder(),

depth = (2, 5), label = 'res\_cells\_repeat'

)

Constructing Fully Connected sequence with two linear layers:

self.avg\_pool = nn.AdaptiveAvgPool2d((1, 1))

self.fc1\_input\_dim = None

self.fc1\_output\_dim = nn.ValueChoice(

\[256, 512\],

label = 'fc1\_output\_dim'

)

self.\_fc1 = None

self.fc2 = nn.Linear(

in\_features = self.fc1\_output\_dim,

out\_features = self.num\_classes

)

242

Chapter 4 Multi-trial Neural arChiteCture SearCh

Defining forward method:

def forward(self, x):

x = self.relu(self.batch\_norm1(self.conv1(x)))

x = self.max\_pool(x)

x = self.res\_cells(x)

x = self.avg\_pool(x)

x = x.reshape(x.shape\[0\], -1)

if not self.fc1\_input\_dim:

self.fc1\_input\_dim = x.shape\[1\]

x = self.relu(self.fc1(x))

x = self.fc2(x)

return x

The following method is used to construct Residual Cells for the Repeat mutator:

@classmethod

def residual\_cell\_builder(cls):

def create\_cell(cell\_num):

Defining Residual Cell parameters:

\# planes sequence: 64, 128, 256, 512,...

planes = 64 \* pow(2, cell\_num)

\# stride sequence: 1, 2, 2, 2,...

stride = max(1 + cell\_num, 2)

Number of Bottleneck blocks in the Residual Cell:

\# block sequence: 3, 4, 5, 5,...

blocks = max(3 + cell\_num, 5)

downsample = None

Placeholder for Bottleneck blocks:

layers = \[\]

243

Chapter 4 Multi-trial Neural arChiteCture SearCh

Constructing downsample identity block if needed:

if stride != 1 or cls.channels != Bottleneck.result\_channels\_

num(planes):

downsample = nn.Sequential(

nn.Conv2d(

in\_channels = cls.channels,

out\_channels = Bottleneck.result\_channels\_

num(planes),

kernel\_size = 1,

stride = stride

),

nn.BatchNorm2d(

num\_features = Bottleneck.result\_channels\_num(planes)

)

)

layers.append(

Bottleneck(

cell\_num = cell\_num,

in\_channels = cls.channels,

out\_channels = planes,

i\_downsample = downsample,

stride = stride

)

)

cls.channels = Bottleneck.result\_channels\_num(planes)

Generating sequence of Bottleneck blocks:

for i in range(blocks - 1):

layers.append(

Bottleneck(

cell\_num = cell\_num,

in\_channels = cls.channels,

out\_channels = planes

)

244

Chapter 4 Multi-trial Neural arChiteCture SearCh

)

return nn.Sequential(\*layers)

return create\_cell

Phew. It was not easy to follow the definition of ResNet Model Space if you are not familiar with ResNet yet. Anyway, don’t forget that NAS treats the neural network as Data Flow Graph, and it tries to find the optimal combination of nodes and connections in the Model Space we constructed in Figure [4-23](#index_split_002.html#p251). Even if some deep learning concepts are not familiar to you yet, try to treat the NAS as the search for the optimal subgraph in supergraph space.

ResNet model evaluator is a classical neural network train–test algorithm. You can examine its code here: ch4/retiarii/cifar\_10\_resnet/eval.py. ResNet NAS Experiment script does not differ too much from LeNet NAS, and I don’t provide its code in the book. Please refer to the script file: ch4/retiarii/cifar\_10\_resnet/run\_cifar10\_resnet\_

experiment.py.

The experiment can be run as follows:

$ python3 ch4/retiarii/cifar\_10\_resnet/run\_cifar10\_resnet\_experiment.py

**Note** Duration ~ 60 hours on intel Core i7 with CuDa (GeForce GtX 1050)

The best model shows **0.957** accuracy on test dataset. That is not perfect, but a much better result than LeNet NAS produced (**0.84**). The best neural network architecture has the following parameters:

{

"pool\_size": 2,

"res\_cells\_repeat": 5,

"bottle\_neck\_0\_skip\_connection": 1,

"bottle\_neck\_1\_skip\_connection": 0,

"bottle\_neck\_2\_skip\_connection": 0,

"bottle\_neck\_3\_skip\_connection": 0,

"bottle\_neck\_4\_skip\_connection": 0,

"fc1\_output\_dim": 512

}

245

Chapter 4 Multi-trial Neural arChiteCture SearCh

These parameters mean that the best model has the sequence of five Residual Cells: the first cell is not using the skipping connection technique, and the others use it. This is a predictable result because usually skipping connection technique raises neural network performance.

In this section, we have achieved a great result! CIFAR-10 is a highly complex

computer vision problem, and even large, sophisticated neural networks cannot

reach high accuracy with this dataset. Table [4-2](#index_split_002.html#p259) compares the architecture we have constructed in this section with other common architectures.

***Table 4-2.** Rating of the best architectures for CIFAR-10*

**Rank**

**Architecture**

**Accuracy**

79

autoDropout

96.8

96

Wide resNet

96.11

**\-**

**Multi-trial NAS ResNet Result**

**95.7**

104

SimpleNetv1

95.51

108

MomentumNet

95.18

116

VGG-19 with Gradinit

94.71

128

tree+Max-avg pooling

94

For more detailed information concerning architecture performance on the

CIFAR- 10 problem, please refer to [https://paperswithcode.com/sota/image-](https://paperswithcode.com/sota/image-classification-on-cifar-10)

[classification- on-cifar-10.](https://paperswithcode.com/sota/image-classification-on-cifar-10)

**Classic Neural Architecture Search (TensorFlow)**

Classic NAS implements the Multi-trial NAS approach. Evaluator takes a model from Model Space and evaluates it separately. Last valid documentation regarding Classic NAS with NNI can be found her[e: https://nni.readthedocs.io/en/v2.2/nas.](https://nni.readthedocs.io/en/v2.2/nas.html)

[html](https://nni.readthedocs.io/en/v2.2/nas.html). NNI currently supports Classic NAS but is deprecating it in favor of the Retiarii framework. The procedure of Classic NAS algorithms is similar to hyperparameter

tuning. Users use nnictl to start experiments, and each model runs as a trial. The difference is that the search space file is automatically generated from the Model Space by running nnictl ss\_gen.

246

Chapter 4 Multi-trial Neural arChiteCture SearCh

The main logical entities of Classic NAS are *Base Model*, *Mutator*, *Search Space*, *Trial*, and *Search Strategy*. Let’s study each of them by applying NAS algorithm to the classical MNIST problem.

**Base Model**

Every Neural Architecture Search starts with defining a Base Model. The Base Model is a neural network that acts as a starting point for new architectures. The Base Model can be very simple or very complex. The researcher chooses the model that is most suitable as a baseline.

Let’s examine the classic LeNet model for the MNIST problem in Listin[g 4-13](#index_split_002.html#p260).

***Listing 4-13.*** Base Model. ch4/classic/base\_model.py

class LeNetModel(Model):

Base Model layers:

def \_\_init\_\_(self):

super().\_\_init\_\_()

self.conv1 = Conv2D(6, 3, padding = 'same', activation = 'relu')

self.pool = MaxPool2D(2)

self.conv2 = Conv2D(16, 3, padding = 'same', activation = 'relu')

self.bn = BatchNormalization()

self.gap = AveragePooling2D(2)

self.fc1 = Dense(120, activation = 'relu')

self.fc2 = Dense(84, activation = 'relu')

self.fc3 = Dense(10)

Feed forward:

def call(self, x):

batch\_size = x.shape\[0\]

x = self.conv1(x)

x = self.pool(x)

x = self.conv2(x)

247

Chapter 4 Multi-trial Neural arChiteCture SearCh

x = self.pool(self.bn(x))

x = self.gap(x)

x = tf.reshape(x, \[batch\_size, -1\])

x = self.fc1(x)

x = self.fc2(x)

x = self.fc3(x)

return x

The model described in Listing [4-13 w](#index_split_002.html#p260)ill serve as a piece of clay for new architectures.

**Mutators**

Mutator transforms the Base Model into a new one. A set of mutators allow defining a search space for the NAS. Classic NNI NAS provides two mutators: LayerChoice and InputChoice. LayerChoice mutator forms the candidate layers for a layer placeholder.

One of the candidates is tried in the exploration process. InputChoice tries different connections. It takes several tensors and chooses n\_chosen tensors from them.

You can learn more about LayerChoice and InputChoice mutators in the subsection

“Mutators” under the section “Neural Architecture Search Using Retiarii (PyTorch).”

We can apply LayerChoice and InputChoice mutators to the Base Model in the

following way.

***Listing 4-14.*** LeNet Model Space. ch4/classic/model.py

class LeNetModelSpace(Model):

def \_\_init\_\_(self):

super().\_\_init\_\_()

We try three different convolution layers for the conv1 placeholder:

self.conv1 = LayerChoice(\[

Conv2D(6, 3, padding = 'same', activation = 'relu'),

Conv2D(6, 5, padding = 'same', activation = 'relu'),

Conv2D(6, 7, padding = 'same', activation = 'relu'),

\], key = 'conv1')

248

Chapter 4 Multi-trial Neural arChiteCture SearCh

We try two different pooling layers for the pool placeholder:

self.pool = LayerChoice(\[

MaxPool2D(2),

MaxPool2D(3)\],

key = 'pool'

)

We try three different convolution layers for the conv2 placeholder:

self.conv2 = LayerChoice(\[

Conv2D(16, 3, padding = 'same', activation = 'relu'),

Conv2D(16, 5, padding = 'same', activation = 'relu'),

Conv2D(16, 7, padding = 'same', activation = 'relu'),

\], key = 'conv2')

self.conv3 = Conv2D(16, 1)

We add skip connection technique:

self.skip\_connect = InputChoice(

n\_candidates = 2,

n\_chosen = 1,

key = 'skip\_connect'

)

self.bn = BatchNormalization()

self.gap = AveragePooling2D(2)

self.fc1 = Dense(120, activation = 'relu')

We add two candidates for fc1 placeholder:

self.fc2 = LayerChoice(\[

Dense(84, activation = 'relu'),

Layer()

\], key = 'fc2')

self.fc3 = Dense(10)

Figur[e 4-24 demons](#index_split_002.html#p263)trates the set of all possible architectures described by Listin[g 4-14.](#index_split_002.html#p261)

249

![](index-263_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-24.** Set of all possible architectures*

We see that each mutator adds variance to the Base Model.

**Trial**

NAS Trial means the same as the Trial in the HPO context. It initializes the model, trains it, tests it, and returns model accuracy. There is only one new feature: you must use the get\_and\_apply\_next\_architecture method from nn.algorithms.nas.tensorflow.

classic\_nas package to initialize the model. Listin[g 4-15 pr](#index_split_002.html#p264)ovides the NAS Trial.

(Full code is provided in the corresponding file: *ch4/classic/trial.py*.) 250

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Listing 4-15.*** NAS Trial.

net = LeNetModelSpace()

get\_and\_apply\_next\_architecture(net)

train\_model(net, dataset\_train, optimizer, epochs)

acc = test\_model(net, dataset\_test)

nni.report\_final\_result(acc.numpy())

**Search Space**

After the Trial script is defined, you should generate the search space JSON file manually using the following command:

$ nnictl ss\_gen --trial\_command="python3 trial.py" --trial\_dir=ch4/classic

\--file=ch4/classic/search\_space.json

The preceding command generates the file shown in Listin[g 4-16.](#index_split_002.html#p264)

***Listing 4-16.*** NAS search space

{

"conv1": {

"\_type": "layer\_choice",

"\_value": \["0", "1", "2"\]

},

"conv2": {

"\_type": "layer\_choice",

"\_value": \["0", "1", "2"\]

},

"fc2": {

"\_type": "layer\_choice",

"\_value": \["0", "1"\]

},

"pool": {

"\_type": "layer\_choice",

"\_value": \["0", "1"\]

},

251

Chapter 4 Multi-trial Neural arChiteCture SearCh

"skip\_connect": {

"\_type": "input\_choice",

"\_value": {

"candidates": \["",""\],

"n\_chosen": 1

}

}

}

As you can see, NNI Classic NAS implementation is pretty close to HPO

implementation. The search space file is a list of all possible neural architecture choices.

**Search Strategy**

Classic NAS supports the following Search Strategies:

• Random Search

• PPO Tuner: Reinforcement Learning Tuner based on Proximal Policy

Optimization algorithm

For more information about these tuners, you can refer to the subsection

“Exploration Strategies” under the section “Neural Architecture Search Using Retiarii (PyTorch).”

**Experiment**

The last thing left to do is to define the experiment configuration. Experiment

configuration is defined in Listin[g 4-17](#index_split_002.html#p265).

***Listing 4-17.*** NAS configuration file

experimentName: example\_mnist

trialConcurrency: 1

maxTrialNum: 100

trainingServicePlatform: local

searchSpacePath: search\_space.json

252

Chapter 4 Multi-trial Neural arChiteCture SearCh

tuner:

builtinTunerName: PPOTuner

classArgs:

optimize\_mode: maximize

trial:

command: python3 trial.py

And now, we can start the experiment with the following command:

$ nnictl create --config=ch4/classic/config.yml

**Note** Duration ~ 2 hours on intel Core i7 with CuDa (GeForce GtX 1050)

Experiment returns the best accuracy **0.9923** on test dataset, with the following parameter set:

conv1: 2

pool: 0

conv2: 0

fc2: 0

skip\_connect: 0

The preceding parameters can be interpreted as the following neural architecture: self.conv1 = LayerChoice(\[

Conv2D(6, 3, ...),

Conv2D(6, 5, ...),

**Conv2D(6, 7, ...), # <- 2**

\], key = ' **conv1**')

self.pool = LayerChoice(\[

**MaxPool2D(2), # <- 0**

MaxPool2D(3)\],

key = ' **pool**'

)

253

Chapter 4 Multi-trial Neural arChiteCture SearCh

self.conv2 = LayerChoice(\[

**Conv2D(16, 3, ...), # <- 0**

Conv2D(16, 5, ...),

Conv2D(16, 7, ...),

\], key = ' **conv2**')

self.fc2 = LayerChoice(\[

**Dense(84, activation = 'relu'), # <- 0**

Layer()

\], key = ' **fc2**')

x0 = self.skip\_connect(\[

**x0, # <- 0**

None\]

)

The best neural architecture is shown in Figure [4-25](#index_split_002.html#p268).

254

![](index-268_1.png)

Chapter 4 Multi-trial Neural arChiteCture SearCh

***Figure 4-25.** Best neural architecture*

Classic NAS does not differ too much from the HPO approach. Indeed, we could build the same experiment with layer and design hyperparameter search. We made a close trick in Chapt[er 2](https://doi.org/10.1007/978-1-4842-8149-9_2), in the section “From LeNet to AlexNet.” Neural Architecture Search has made great strides lately, and Classic NAS cannot support new research ideas. In any case, you can still use Classic NAS and get meaningful results by searching for new solutions.

255

Chapter 4 Multi-trial Neural arChiteCture SearCh

**Summary**

Multi-trial Neural Architecture Search using Retiarii and classic approaches offers clear and elegant solutions for searching robust neural architectures. Many meaningful results could be achieved using Multi-trial NAS. But this approach has one very serious drawback. It takes too much time. Indeed, complex models and massive datasets need too much time to train, and the Model Space can contain millions of model samples.

Even the most advanced Exploration Strategy can take too much time to converge to some suboptimal neural architecture. But the time problem has a solution called Oneshot NAS, and we will explore this method in the next chapter.

256

**CHAPTER 5**

**One-Shot Neural**

**Architecture Search**

In the previous chapter, we explored Multi-trial Neural Architecture Search, which is a very promising approach. And the reader might wonder why Multi-trial NAS is called that way. Are there any other non-Multi-trial NAS approaches, and is it really possible to search for the optimal neural network architecture in some other way without trying it? It looks pretty natural that the only way to find the optimal solution is to try different elements in the search space. In fact, it turns out that this is not entirely true. There is an approach that allows you to find the best architecture by training some Supernet. And this approach is called **One-shot Neural Architecture Search**. As the name “one-shot”

implies, this approach involves only one try or shot. Of course, this “shot” is much longer than single neural network training, but nevertheless, it saves a lot of time.

In this chapter, we will study what One-shot NAS is and how to design architectures for this approach. We will examine two popular One-shot algorithms: **Efficient Neural** **Architecture Search via Parameter Sharing** (**ENAS**) and **Differentiable Architecture** **Search** (**DARTS**). Of course, we will apply these algorithms to solve practical problems.

NNI 2.7 version (which is used in this book) has ENAS algorithm implementation

for the TensorFlow framework, but it doesn’t have one for the DARTS algorithm. Anyway, ENAS algorithm is one of the most popular and efficient One-shot NAS implementations, so TensorFlow users shouldn’t get too frustrated.

**One-Shot NAS in Action**

Interest in automating neural network architecture design is growing, but the classical Multi-trial NAS approach is too computationally expensive, requiring thousands and millions of different architectures to be trained from scratch. This fact, unfortunately, 257

© Ivan Gridin 2022

I. Gridin, *Automated Deep Learning Using Neural Network Intelligence*,

[https://doi.org/10.1007/978-1-4842-8149-9\_5](https://doi.org/10.1007/978-1-4842-8149-9_5#DOI)

![](index-271_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

makes Multi-trial NAS not applicable in practice. Indeed, some Multi-trial experiments can take weeks or months on the most modern computing resources. A new Oneshot NAS approach has been proposed to address this weakness of Multi-trial

architecture search.

The best way to introduce One-shot NAS is to provide an example. Let’s say we are looking for the optimal architecture for the MNIST problem. And we have the Model Space shown in Figure [5-1](#index_split_002.html#p271).

***Figure 5-1.** Model Space for MNIST problem*

Figur[e 5-1 sho](#index_split_002.html#p271)ws the Model Space with two mutable layers. Each mutable layer has the following choices: Conv 1×1, Conv 3×3, and Conv 5×5. In a classic Multi-shot scenario, we would perform 3×3=9 trials for each combination of parameters and pick the best one. While the One-shot NAS approach follows another technique, we create one *Supernet* that merges or reduces the output of each mutable layer and train the resulting neural network only once. Figure [5-2](#index_split_002.html#p272) demonstrates this Supernet.

258

![](index-272_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-2.** Supernet for MNIST problem*

After training the Supernet, we evaluate it by activating each combination of layers and zeroing out other layers. Figure [5-3](#index_split_002.html#p273) illustrates this concept.

259

![](index-273_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-3.** Supernet for MNIST problem*

And finally, we pick the combination which demonstrated the best performance.

This combination represents the result of the One-shot NAS algorithm. For example, if a combination (Conv 5×5, Conv 5×5) showed the best accuracy, then our target network design is Conv 5×5 → Conv 5×5 → Linear → Linear.

Let’s summarize what exactly we did during the One-shot NAS algorithm:

• We created a single *Supernet* derived from Model Space.

• We *trained* it.

• We *evaluated* it nine times, activating different layers in turn.

• We picked the *best* neural design for the problem.

The main benefit we have here is that we trained Supernet only once instead of

training each of nine candidate networks! It speeds up the whole neural architecture search dramatically, because the network training is the longest part of NAS process.

A reader may have a fair question: *“But wait! We trained a single Supernet network.*

*All candidate layers learned to work together! But then we decided to break it into different* *parts, leaving the same weights. This is nonsense!”* I agree. This is a very counterintuitive concept. Indeed, all layers were trained together, and they learned to complement and help each other in solving the problem. Surely you can’t just throw out some layers from a neural network searching for the best architecture. But the most fantastic thing about One-shot NAS is that you can! There is still no sufficient mathematical basis for this 260

Chapter 5 One-ShOt neural arChiteCture SearCh

approach, but it works in practice. Let’s implement this approach in practice using the example we considered earlier. In this section, we will not be using the NNI toolkit. Here, our goal is to get an intuition about the One-shot NAS approach.

To begin with, we will make a vanilla Multi-trial NAS. Listing [5-1](#index_split_002.html#p274) (TensorFlow implementation) and Listin[g 5-2 (P](#index_split_002.html#p275)yTorch implementation) implement the model shown in Figure [5-1](#index_split_002.html#p271).

We import necessary modules:

***Listing 5-1.*** **TensorFlow** implementation. Model Space. ch5/naive\_one\_shot\_

nas/tf/tf\_lenet\_multi\_model.py

from tensorflow.keras import Model

from tensorflow.keras.layers import Dense, Flatten, MaxPool2D

from ch5.naive\_one\_shot\_nas.tf.tf\_ops import create\_conv

The following model accepts two parameters, kernel1 and kernel2, that define the conv1 and conv2 layers:

class TfLeNetMultiTrialModel(Model):

def \_\_init\_\_(self, **kernel1**, **kernel2**):

super().\_\_init\_\_()

self. **conv1** = **create\_conv**(**kernel1**, filter = 16)

self.pool1 = MaxPool2D(pool\_size = 2)

self. **conv2** = **create\_conv**(**kernel2**, filter = 32)

self.pool2 = MaxPool2D(pool\_size = 2)

self.flatten = Flatten()

self.fc1 = Dense(128, 'relu')

self.fc2 = Dense(10, 'softmax')

def call(self, x, \*\*kwargs):

x = self.conv1(x)

x = self.pool1(x)

x = self.conv2(x)

x = self.pool2(x)

x = self.flatten(x)

x = self.fc1(x)

return self.fc2(x)

261

Chapter 5 One-ShOt neural arChiteCture SearCh

We import necessary modules:

***Listing 5-2.*** **PyTorch** implementation. Model Space. ch5/naive\_one\_shot\_nas/

pt/pt\_lenet\_multi\_model.py

import torch

import torch.nn as nn

import torch.nn.functional as F

from ch5.naive\_one\_shot\_nas.pt.pt\_ops import create\_conv

The following model below accepts two parameters, kernel1 and kernel2, that

define the conv1 and conv2 layers:

class PtLeNetMultiTrialModel(nn.Module):

def \_\_init\_\_(self, **kernel1**, **kernel2**):

super(PtLeNetMultiTrialModel, self).\_\_init\_\_()

self. **conv1** = **create\_conv**(**kernel1**, in\_channels = 1, out\_channels = 16) self. **conv2** = **create\_conv**(**kernel2**, in\_channels = 16, out\_channels = 32) self.flat = nn.Flatten()

self.fc1 = nn.Linear(1568, 128)

self.fc2 = nn.Linear(128, 10)

def forward(self, x):

x = torch.relu(self.conv1(x))

x = F.max\_pool2d(x, 2, 2)

x = torch.relu(self.conv2(x))

x = F.max\_pool2d(x, 2, 2)

x = self.flat(x)

x = torch.relu(self.fc1(x))

x = self.fc2(x)

return F.log\_softmax(x, dim = 1)

And now, let’s execute Multi-trial NAS iterating through the various kernel\_size parameters (kernel1: \[1, 3, 5\], kernel2: \[1, 3, 5\]) using the script in Listing [5-3](#index_split_002.html#p276)

(TensorFlow implementation) and Listing [5-4](#index_split_002.html#p276) (PyTorch implementation).

262

Chapter 5 One-ShOt neural arChiteCture SearCh

We import necessary modules:

***Listing 5-3.*** **TensorFlow** implementation. Multi-trial NAS. ch5/naive\_one\_shot\_

nas/tf/ms\_search.py

from ch5.naive\_one\_shot\_nas.tf.tf\_lenet\_multi\_model import

TfLeNetMultiTrialModel

from ch5.naive\_one\_shot\_nas.tf.tf\_train import train, test

Defining the search space:

kernel1\_choices = \[1, 3, 5\]

kernel2\_choices = \[1, 3, 5\]

results = {}

Performing Multi-trial search:

for k1 in kernel1\_choices:

for k2 in kernel2\_choices:

\# Trial

model = TfLeNetMultiTrialModel(k1, k2)

train(model)

accuracy = test(model)

results\[(k1, k2)\] = accuracy

Displaying results:

print('=======')

print('Results:')

for k, v in results.items():

print(f'Conv1 {k\[0\]}x{k\[0\]}, Conv2: {k\[1\]}x{k\[1\]} : {v}')

We import necessary modules:

***Listing 5-4.*** **PyTorch** implementation. Multi-trial NAS. ch5/naive\_one\_shot\_

nas/pt/ms\_search.py

from ch5.naive\_one\_shot\_nas.pt.pt\_lenet\_multi\_model import

PtLeNetMultiTrialModel

from ch5.naive\_one\_shot\_nas.pt.pt\_train import train\_model, test\_model

263

Chapter 5 One-ShOt neural arChiteCture SearCh

Defining the search space:

kernel1\_choices = \[1, 3, 5\]

kernel2\_choices = \[1, 3, 5\]

results = {}

Performing Multi-trial search:

for k1 in kernel1\_choices:

for k2 in kernel2\_choices:

\# Trial

model = PtLeNetMultiTrialModel(k1, k2)

train\_model(model)

accuracy = test\_model(model)

results\[(k1, k2)\] = accuracy

Defining the search space:

print('=======')

print('Results:')

for k, v in results.items():

print(f'Conv1 {k\[0\]}x{k\[0\]}, Conv2: {k\[1\]}x{k\[1\]} : {v}')

The results of the Multi-trial NAS we performed are listed in Ta[ble 5-1.](#index_split_002.html#p277)

***Table 5-1.** Multi-trial NAS results*

**Trial**

**Conv1**

**Conv2**

**Accuracy**

1

Conv1×1

Conv1×1

0.9446

2

Conv1×1

Conv3×3

0.9849

3

Conv1×1

Conv5×5

0.9864

4

Conv3×3

Conv3×3

0.9851

5

Conv3×3

Conv3×3

0.9881

6

Conv3×3

Conv5×5

0.9909

7

Conv5×5

Conv1×1

0.9872

8

Conv5×5

Conv3×3

0.9901

**9**

**Conv5×5**

**Conv5×5**

**0.9917**

264

Chapter 5 One-ShOt neural arChiteCture SearCh

According to Table [5-1](#index_split_002.html#p277), the best candidate is (Conv5×5, Conv5×5). Well, we tried every neural design candidate and found the most suitable one for the MNIST problem.

Of course, the Multi-trial NAS we implemented earlier is quite simple, but that’s how all Multi-trial approaches act in general.

But for now, let’s try to get the same result using the One-shot NAS approach!

First, we create the Supernet model depicted in Figur[e 5-2 (in L](#index_split_002.html#p272)isting [5-5](#index_split_002.html#p278) \[TensorFlow implementation\] and Listin[g 5-6 \[P](#index_split_002.html#p279)yTorch implementation\]).

We import necessary modules:

***Listing 5-5.*** **TensorFlow** implementation. Supernet. ch5/naive\_one\_shot\_nas/

tf/tf\_lenet\_supernet.py

from tensorflow.keras import Model

from tensorflow.keras.layers import Dense, Flatten, MaxPool2D

from ch5.naive\_one\_shot\_nas.tf.tf\_ops import create\_conv

TfLeNetNaiveSupernet implements Supernet depicted in Figure [5-2](#index_split_002.html#p272): class TfLeNetNaiveSupernet(Model):

def \_\_init\_\_(self):

super().\_\_init\_\_()

We define each candidate for conv1 and conv2 layers:

self.conv1\_1 = create\_conv(1, 16)

self.conv1\_3 = create\_conv(3, 16)

self.conv1\_5 = create\_conv(5, 16)

self.conv2\_1 = create\_conv(1, 32)

self.conv2\_3 = create\_conv(3, 32)

self.conv2\_5 = create\_conv(5, 32)

Next are the other Supernet layers:

self.pool1 = MaxPool2D(pool\_size = 2)

self.pool2 = MaxPool2D(pool\_size = 2)

self.flatten = Flatten()

self.fc1 = Dense(128, 'relu')

self.fc2 = Dense(10, 'softmax')

265

Chapter 5 One-ShOt neural arChiteCture SearCh

call method accepts mask parameter, which activates candidate layer in a sum merge operation. The mask parameter is not passed in the training mode, and all candidates are summed:

x = 1×conv1\_1(x) + 1×conv1\_3(x) + 1×conv1\_5(x)

x = 1×conv2\_1(x) + 1×conv2\_3(x) + 1×conv2\_5(x).

But in evaluation mode, we pass mask parameter and activate only particular layers: x = 0×conv1\_1(x) + **1**×**conv1\_3(x)** + 0×conv1\_5(x)

x = 0×conv2\_1(x) + 0×conv2\_3(x) + **1**×**conv2\_5(x)**:

def call(self, x, **mask** = None):

\# Sum all in training mode

if mask is None:

mask = \[\[1, 1, 1\], \[1, 1, 1\]\]

x = mask\[0\]\[0\] \* self.conv1\_1(x) +\\

mask\[0\]\[1\] \* self.conv1\_3(x) +\\

mask\[0\]\[2\] \* self.conv1\_5(x)

x = self.pool1(x)

x = mask\[1\]\[0\] \* self.conv2\_1(x) +\\

mask\[1\]\[1\] \* self.conv2\_3(x) +\\

mask\[1\]\[2\] \* self.conv2\_5(x)

x = self.pool2(x)

x = self.flatten(x)

x = self.fc1(x)

return self.fc2(x)

We import necessary modules:

***Listing 5-6.*** **PyTorch** implementation. Supernet. ch5/naive\_one\_shot\_nas/pt/

pt\_lenet\_supernet.py

import torch

import torch.nn as nn

import torch.nn.functional as F

from ch5.naive\_one\_shot\_nas.pt.pt\_ops import create\_conv

266

Chapter 5 One-ShOt neural arChiteCture SearCh

PtLeNetNaiveSupernet implements Supernet depicted in Figure [5-2](#index_split_002.html#p272): class PtLeNetNaiveSupernet (nn.Module):

def \_\_init\_\_(self):

super(PtLeNetNaiveSupernet, self).\_\_init\_\_()

We define each candidate for conv1 and conv2 layers:

self.conv1\_1 = create\_conv(1, 1, 16)

self.conv1\_3 = create\_conv(3, 1, 16)

self.conv1\_5 = create\_conv(5, 1, 16)

self.conv2\_1 = create\_conv(1, 16, 32)

self.conv2\_3 = create\_conv(3, 16, 32)

self.conv2\_5 = create\_conv(5, 16, 32)

Next are the other Supernet layers:

self.flat = nn.Flatten()

self.fc1 = nn.Linear(1568, 128)

self.fc2 = nn.Linear(128, 10)

forward method accepts mask parameter, which activates candidate layer in a

sum merge operation. The mask parameter is not passed in the training mode, and all candidates are summed:

x = 1×conv1\_1(x) + 1×conv1\_3(x) + 1×conv1\_5(x)

x = 1×conv2\_1(x) + 1×conv2\_3(x) + 1×conv2\_5(x).

But in evaluation mode, we pass mask parameter and activate only particular layers: x = 0×conv1\_1(x) + **1**×**conv1\_3(x)** + 0×conv1\_5(x)

x = 0×conv2\_1(x) + 0×conv2\_3(x) + **1**×**conv2\_5(x)**:

def forward(self, x, **mask** = None):

\# Sum all in training mode

if mask is None:

mask = \[\[1, 1, 1\], \[1, 1, 1\]\]

x = mask\[0\]\[0\] \* self.conv1\_1(x) +\\

mask\[0\]\[1\] \* self.conv1\_3(x) +\\

mask\[0\]\[2\] \* self.conv1\_5(x)

267

Chapter 5 One-ShOt neural arChiteCture SearCh

x = torch.relu(x)

x = F.max\_pool2d(x, 2, 2)

x = mask\[1\]\[0\] \* self.conv2\_1(x) +\\

mask\[1\]\[1\] \* self.conv2\_3(x) +\\

mask\[1\]\[2\] \* self.conv2\_5(x)

x = torch.relu(x)

x = F.max\_pool2d(x, 2, 2)

x = self.flat(x)

x = torch.relu(self.fc1(x))

x = self.fc2(x)

return F.log\_softmax(x, dim = 1)

Next, we train the Supernet and evaluate different candidate layer combinations in Listin[g 5-7 (](#index_split_002.html#p281)TensorFlow implementation) and Listing [5-8](#index_split_002.html#p282) (PyTorch implementation).

We import necessary modules:

***Listing 5-7.*** **TensorFlow** implementation. One-shot NAS. ch5/naive\_one\_shot\_

nas/tf/os\_search.py

import tensorflow as tf

from sklearn.metrics import accuracy\_score

from ch5.datasets import mnist\_dataset

from ch5.naive\_one\_shot\_nas.tf.tf\_lenet\_supernet import

TfLeNetNaiveSupernet

from ch5.naive\_one\_shot\_nas.tf.tf\_train import train

Initializing Supernet:

model = TfLeNetNaiveSupernet()

Training Supernet:

train(model)

Loading test dataset:

\_, (x, y) = mnist\_dataset()

268

Chapter 5 One-ShOt neural arChiteCture SearCh

Evaluating Supernet activating each candidate:

kernel1\_choices = \[1, 3, 5\]

kernel2\_choices = \[1, 3, 5\]

results = {}

for m1 in range(0, len(kernel1\_choices)):

for m2 in range(0, len(kernel2\_choices)):

\# activation mask

mask = \[\[0, 0, 0\], \[0, 0, 0\]\]

\# activating conv1 and conv2 layers

mask\[0\]\[m1\] = 1

mask\[1\]\[m2\] = 1

\# calculating accuracy

output = model(x, mask = mask)

predict = tf.argmax(output, axis = 1)

accuracy = round(accuracy\_score(predict, y), 4)

results\[(kernel1\_choices\[m1\], kernel2\_choices\[m2\])\] = accuracy

Displaying results:

print('=======')

print('Results:')

for k, v in results.items():

print(f'Conv1 {k\[0\]}x{k\[0\]}, Conv2: {k\[1\]}x{k\[1\]} : {v}')

We import necessary modules:

***Listing 5-8.*** **PyTorch** implementation. One-shot NAS. ch5/naive\_one\_shot\_nas/

pt/os\_search.py

import torch

from sklearn.metrics import accuracy\_score

from ch5.datasets import mnist\_dataset

from ch5.naive\_one\_shot\_nas.pt.pt\_lenet\_supernet import

PtLeNetNaiveSupernet

from ch5.naive\_one\_shot\_nas.pt.pt\_train import train\_model

269

Chapter 5 One-ShOt neural arChiteCture SearCh

Initializing Supernet:

model = PtLeNetNaiveSupernet()

Training Supernet:

train\_model(model)

Loading test dataset:

\_, (x, y) = mnist\_dataset()

x = torch.from\_numpy(x).float()

y = torch.from\_numpy(y).long()

x = torch.permute(x, (0, 3, 1, 2))

Evaluating Supernet activating each candidate:

model.eval()

kernel1\_choices = \[1, 3, 5\]

kernel2\_choices = \[1, 3, 5\]

results = {}

for m1 in range(0, len(kernel1\_choices)):

for m2 in range(0, len(kernel2\_choices)):

\# activation mask

mask = \[\[0, 0, 0\], \[0, 0, 0\]\]

\# activating conv1 and conv2 layers

mask\[0\]\[m1\] = 1

mask\[1\]\[m2\] = 1

\# calculating accuracy

output = model(x, mask)

predict = output.argmax(dim = 1, keepdim = True)

accuracy = round(accuracy\_score(predict, y), 4)

results\[(kernel1\_choices\[m1\], kernel2\_choices\[m2\])\] = accuracy

270

Chapter 5 One-ShOt neural arChiteCture SearCh

Displaying results:

print('=======')

print('Results:')

for k, v in results.items():

print(f'Conv1 {k\[0\]}x{k\[0\]}, Conv2: {k\[1\]}x{k\[1\]} : {v}')

The results of the One-shot NAS are listed in Table [5-2](#index_split_002.html#p284).

***Table 5-2.** One-shot NAS results*

**Trial**

**Conv1**

**Conv2**

**Accuracy**

1

Conv1×1

Conv1×1

0.2343

2

Conv1×1

Conv3×3

0.1789

3

Conv1×1

Conv5×5

0.2127

4

Conv3×3

Conv3×3

0.2755

5

Conv3×3

Conv3×3

0.8515

6

Conv3×3

Conv5×5

0.8786

7

Conv5×5

Conv1×1

0.3486

8

Conv5×5

Conv3×3

0.8882

**9**

**Conv5×5**

**Conv5×5**

**0.9001**

The best neural architecture found by One-shot NAS is (Conv 5×5, Conv 5×5),

which is exactly the same as the result of Multi-trial NAS. Incredible, isn’t it? We found the same result in a much shorter time!

**Note** the results presented in t[able 5-2 are only needed to rank various](#index_split_002.html#p284)

combinations of architectures to pick the best one. these results do not

characterize the accuracy of the corresponding combination. One-shot models are

typically only used to rank architectures in the Model Space. the best-performing architectures are retrained from scratch after the search is completed.

271

![](index-285_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

Intuitively, the One-shot NAS approach can be illustrated as follows: *during* *Supernet training, the best performing candidate layers play much more significant* *roles in the Data Flow Graph of the Supernet neural network*. This fact allows finding these candidates by deactivating others during the evaluation process. Figur[e 5-4](#index_split_002.html#p285)

demonstrates this concept.

***Figure 5-4.** Different layer importance in the Supernet*

Since we have an intuition about the One-shot NAS approach, we can start

implementing it using the NNI framework.

**Supernet Architecture**

As we saw in the previous section, one of the main concepts in One-shot NAS is the *Supernet*. Supernet is a single neural network that contains all the various neural network architectures from the defined Model Space. Supernet is trained once according to the One-shot NAS technique, and then the optimal subnet is selected. In Multi-trial NAS, each Data Flow Graph is tried separately. But One-shot NAS creates a single Supernet based on all possible Data Flow Graphs in Model Space.

272

![](index-286_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

NNI creates Model Space for One-shot NAS using LayerChoice and InputChoice

operations. LayerChoice candidates form a special block in the Supernet. Each

LayerChoice candidate transforms input tensor, and then their output tensors are reduced according to a particular One-shot NAS algorithm. The reduce operation

can be sum, mean, or any other operation that merges tensors. InputChoice candidate tensors are reduced in Supernet in the same way as LayerChoice candidates. Figur[e 5-5](#index_split_002.html#p286)

demonstrates Model Space constructed with LayerChoice and InputChoice operations.

***Figure 5-5.** Model Space*

Model Space depicted in Figur[e 5-5](#index_split_002.html#p286) generates Supernet with reduce operations.

Figur[e 5-6 demons](#index_split_002.html#p287)trates Supernet with sum as reduce operations.

273

![](index-287_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-6.** One-shot NAS Supernet*

Supernet is trained according to a specific One-shot NAS algorithm. After the

training, each subnet is evaluated, and the subnetwork with the best accuracy forms the target neural architecture. Figure [5-7](#index_split_002.html#p288) demonstrates the evaluation of a specific subnet.

274

![](index-288_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-7.** Subnet Evaluation*

One-shot NAS sets a strict restriction on the LayerChoice and InputChoice

candidates. Each of the candidates must return a tensor of the same size. Otherwise, it will be impossible to implement the reduce operation. In the previous section, candidates for conv1 layer returned 16×28×28 tensors, and candidates for conv2 layer returned 32×14×14 tensors. Figure [5-8](#index_split_002.html#p289) demonstrates this fact.

275

![](index-289_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-8.** Same size tensor outputs*

This restriction does not exist in Multi-trial NAS since TensorFlow and PyTorch

frameworks allowed layer parameters to be calculated depending on the input tensor; therefore, LayerChoice candidates could return tensors of various sizes. In the case of One-shot NAS, we must be sure that the candidates return tensors of the same size.

Otherwise, the NAS algorithm fails with an error.

Let’s create our first Model Space for One-shot NAS. It will be a “*Hello World*”

model, which we will use to test One-shot NAS algorithms in the next section. We will define Model Space for One-shot search using LeNet architecture variations depicted in Figur[e 5-9.](#index_split_002.html#p290)

276

![](index-290_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-9.** LeNet One-shot Model Space*

NNI implementation for TensorFlow of the Model Space depicted in Figur[e 5-9 is](#index_split_002.html#p290)

provided in Listin[g 5-9.](#index_split_002.html#p290)

LayerChoice and InputChoice methods are implemented in nni.nas.tensorflow.

mutables package:

***Listing 5-9.*** **TensorFlow** implementation. One-shot LeNet NAS. ch5/model/

lenet/tf\_lenet.py

from nni.nas.tensorflow.mutables import InputChoice, LayerChoice

Importing tensorflow.keras modules:

from tensorflow.keras import Model

from tensorflow.keras.layers import Conv2D, Dense, Flatten, MaxPool2D

277

Chapter 5 One-ShOt neural arChiteCture SearCh

Defining helper function creating convolution layer:

def create\_conv(kernel, filters):

return Conv2D(

filters = filters,

kernel\_size = kernel,

activation = 'relu',

padding = 'same'

)

class TfLeNetSupernet(Model):

def \_\_init\_\_(self):

super().\_\_init\_\_()

Setting LayerChoices for conv1 and conv2 layers:

self. **conv1** = LayerChoice(\[

create\_conv(kernel = 1, filters = 16), # 0

create\_conv(kernel = 3, filters = 16), # 1

create\_conv(kernel = 5, filters = 16) # 2

\], key = 'conv1')

self. **conv2** = LayerChoice(\[

create\_conv(kernel = 1, filters = 32), # 0

create\_conv(kernel = 3, filters = 32), # 1

create\_conv(kernel = 5, filters = 32) # 2

\], key = 'conv2')

self.pool = MaxPool2D(2)

self.flat = Flatten()

Setting InputChoice for linear layers:

self.dm = InputChoice(n\_candidates = 2, n\_chosen = 1, key = 'dm')

self.fc11 = Dense(256, activation = 'relu')

self.fc12 = Dense(10, activation = 'softmax')

self.fc2 = Dense(10, activation = 'softmax')

278

Chapter 5 One-ShOt neural arChiteCture SearCh

Defining call method:

def **call**(self, x):

x = self.conv1(x)

x = self.pool(x)

x = self.conv2(x)

x = self.pool(x)

x = self.flat(x)

\# branch 1

x1 = self.fc12(self.fc11(x))

\# branch 2

x2 = self.fc2(x)

\# Choosing one of the branches

x = self.dm(\[

x1, # 0

x2 # 1

\])

return x

NNI implementation for PyTorch of the Model Space depicted in Figure [5-9](#index_split_002.html#p290) is provided in Listin[g 5-10](#index_split_002.html#p292).

LayerChoice and InputChoice methods are implemented in nni.retiarii.nn.pytorch

package:

***Listing 5-10.*** **PyTorch** implementation. One-shot LeNet NAS. ch5/model/lenet/

pt\_lenet.py

from nni.retiarii.nn.pytorch import LayerChoice, InputChoice

Importing other modules:

from typing import OrderedDict

import torch.nn as nn

import torch.nn.functional as F

279

Chapter 5 One-ShOt neural arChiteCture SearCh

Defining helper function creating convolution layer:

def create\_conv(kernel, in\_ch, out\_ch):

return nn.Conv2d(

in\_channels = in\_ch,

out\_channels = out\_ch,

kernel\_size = kernel,

padding = int((kernel - 1) / 2)

)

class PtLeNetSupernet(nn.Module):

def \_\_init\_\_(self, input\_ts = 32):

super(PtLeNetSupernet, self).\_\_init\_\_()

Setting LayerChoices for conv1 and conv2 layers:

self. **conv1** = LayerChoice(OrderedDict(

\[

('conv1x1->16', create\_conv(1, 1, 16)), # 0

('conv3x3->16', create\_conv(3, 1, 16)), # 1

('conv5x5->16', create\_conv(5, 1, 16)), # 2

\]

), label = 'conv1')

self. **conv2** = LayerChoice(OrderedDict(

\[

('conv1x1->32', create\_conv(1, 16, 32)), # 0

('conv3x3->32', create\_conv(3, 16, 32)), # 1

('conv5x5->32', create\_conv(5, 16, 32)), # 2

\]

), label = 'conv2')

self.act = nn.ReLU()

self.flat = nn.Flatten()

280

Chapter 5 One-ShOt neural arChiteCture SearCh

Setting InputChoice for linear layers:

self.dm = InputChoice(n\_candidates = 2, n\_chosen = 1, label = 'dm')

self.fc11 = nn.Linear(input\_ts \* 8 \* 8, 256)

self.fc12 = nn.Linear(256, 10)

self.fc2 = nn.Linear(input\_ts \* 8 \* 8, 10)

Defining forward method:

def **forward**(self, x):

x = self.act(self.conv1(x))

x = F.max\_pool2d(x, 2, 2)

\# x.shape = (16, 16, 16)

x = self.act(self.conv2(x))

x = F.max\_pool2d(x, 2, 2)

\# x.shape = (32, 8, 8)

x = self.flat(x)

\# branch 1

x1 = self.act(self.fc11(x))

x1 = self.act(self.fc12(x1))

\# branch 2

x2 = self.act(self.fc2(x))

\# Choosing one of the branches

x = self.dm(\[

x1, # 0

x2 # 1

\])

return F.log\_softmax(x, dim = 1)

Since we defined One-shot Model Space using NNI, we can move on to

implementing advanced One-shot algorithms.

281

Chapter 5 One-ShOt neural arChiteCture SearCh

**One-Shot Algorithms**

At the moment, One-shot NAS is a young area and is developing rapidly. Many

algorithms that implement the One-shot concept are being invented at the moment.

This section will study two of the most popular One-shot algorithms: Efficient Neural Architecture Search (ENAS) and Differentiable Architecture Search (DARTS).

**Efficient Neural Architecture Search (ENAS)**

Efficient Neural Architecture Search (ENAS) is a fast and inexpensive approach for automatic model design. In ENAS, a controller discovers neural network architectures by searching for an optimal subnet within a large Supernet. The controller is trained with a policy gradient to select a subnet that maximizes the expected reward on a validation set. Meanwhile, the model corresponding to the selected subnet is trained to minimize the loss function. Sharing parameters among child models allows ENAS to deliver strong empirical performances. It uses much fewer GPU hours than classical Multi-trial NAS

approaches.

The original paper “Efficient Neural Architecture Search via Parameter Sharing”

( [*https://arxiv.org/pdf/1802.03268.pdf*) h](https://arxiv.org/pdf/1802.03268.pdf)as a lot of formulas and can be too complicated. Let’s study the idea of this approach in a more practical way.

One of the key concepts in ENAS is Reinforcement Learning Controller or RL

Controller or simply Controller. RL Controller contains a neural network *θ* that learns how to extract the most efficient subnets from the Supernet. The main task of the RL

Controller is to find the optimal subnet in the Supernet, and it is trained according to the Reinforcement Learning algorithm. The Controller creates a subnet by defining a binary mask, where 1 activates layer and 0 disables it. Figur[e 5-10 sho](#index_split_002.html#p296)ws how RL Controller selects subnet from the Supernet using binary mask.

282

![](index-296_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-10.** RL Controller subnet selection*

RL Controller picks a subnet and runs one or several training epochs. The core of the ENAS approach is the weight-sharing technique. The same layers in different subnets share the same weights. When Controller picks a subnet, it is not being trained from scratch; layers share weights that have already been trained. Weight-sharing concept is demonstrated in Figure [5-11.](#index_split_002.html#p297)

283

![](index-297_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-11.** Weight sharing*

The weight-sharing approach allows the Controller to find the best architecture

with small iterations and without retraining a new subnet from scratch each time. ENAS

algorithm can be demonstrated using the following pseudo-code:

We initialize a Supernet: S

And load train and validation datasets: train\_ds, val\_ds

Next, the algorithm initializes ENAS Controller (Controller(S, θ)), where *θ* denotes Controller weights that help choose optimal subnet from S Supernet:

Ctrl = Controller(S, θ)

Main training loop:

for epoch in epochs:

1\. Supernet training loop:

for batch in batches(train\_ds):

284

Chapter 5 One-ShOt neural arChiteCture SearCh

i. Controller implements stochastic policy, which means that it

operates with probabilities. The most promising subnet has

the highest probability to be chosen:

s ← Ctrl.sample() #picks pseudo-random subnet

ii. Subnet network is trained once (i.e., only one training

epoch) on a training batch using weight-sharing technique

(Figure [5-11):](#index_split_002.html#p297)

train\_once(subnet, batch)

2\. Controller training loop. In this loop, Controller learns how to

find a subnet that gives the highest reward, that is, accuracy on

validation dataset:

for batch in batches(val\_ds):

i. Controller chooses subnet and calculates its accuracy on

validation dataset batch:

subnet ← Ctrl.sample() #picks pseudo random subnet

reward = test(subnet, batch)

ii. Controller collects experience about subnet performance:

Ctrl.add\_experience(reward)

3\. Controller updates its weights *θ* according to new experience:

Ctrl.self\_update\_with\_new\_experience()

\# end of main training loop

After training, Controller returns the best subnet:

Ctrl.best()

285

Chapter 5 One-ShOt neural arChiteCture SearCh

In the algorithm described earlier, the Controller trains various subnets on the training dataset and then tests them on the validation dataset. By repeating this process many times, the Controller understands which architectures show the best accuracy and gradually reduces the exploration process to a limited number of architectures. At the end of the training process, the Controller converges to one or several of the best architectures.

Let’s see how ENAS works in practice:

1\. Initially, the Controller has no assumptions about subnets, and it

chooses random subnets for single training (subnet is trained for

one training epoch only) using the weight-sharing technique as

depicted in Figure [5-11.](#index_split_002.html#p297)

2\. After, Controller generates subnets based on *θ* weights and

collects accuracy on the validation dataset.

3\. Based on experience gained in step 2, Controller updates *θ* values.

Figur[e 5-12 demons](#index_split_002.html#p300)trates steps 1–3 we described earlier.

286

![](index-300_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-12.** ENAS in action. Initial epoch*

Next, Controller chooses the most promising subnets to train using the weight-

sharing technique and tests their accuracy on the validation dataset, as shown in Figur[e 5-13.](#index_split_002.html#p301)

287

![](index-301_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-13.** ENAS in action. Middle training*

After training Supernet layers separately and updating *θ* experience, Controller converges to some subnet that it considers the best. Figur[e 5-14](#index_split_002.html#p302) illustrates it.

288

![](index-302_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-14.** ENAS in action. End training*

One-shot ENAS algorithm is close to RL Strategy from Multi-trial NAS, but with one significant difference. ENAS does not make a complete subnet training cycle but uses weight sharing and incremental one-step training. This difference dramatically speeds up the process of finding the best architecture.

NNI implements ENAS using the following classes:

• **PyTorch**: nni.retiarii.oneshot.pytorch.enas.EnasTrainer

• **TensorFlow**: nni.algorithms.nas.tensorflow.enas.EnasTrainer

289

Chapter 5 One-ShOt neural arChiteCture SearCh

Table [5-3](#index_split_002.html#p303) shows EnasTrainer parameters.

***Table 5-3.** EnasTrainer parameters*

**Parameter**

**Description**

model

pytorch or tensorFlow model to be trained

loss

Type: callable

loss function

metrics

Type: callable

Measures model accuracy

reward\_function

Type: callable

is used by enaS Controller to calculate reward. usually, reward\_function

returns model accuracy

optimizer

Type: Optimizer

Optimizer for model training

num\_epochs

Type: int

number of epochs planned for training

dataset

Type: Dataset

training dataset

batch\_size

Type: int, Default: 64

training batch size

workers

Type: int, Default: 4

Workers for data loading

log\_frequency

Type: int, Default: None

logging step count

grad\_clip

Type: float, Default: 5.0

Gradient clipping. Set to 0 to disable

entropy\_weight

Type: float, Default: 0.0001

Sample entropy loss weight

skip\_weight

Type: float, Default: 0.8

Skip penalty loss weight

( *continued*)

290

Chapter 5 One-ShOt neural arChiteCture SearCh

***Table 5-3.*** ( *continued*)

**Parameter**

**Description**

baseline\_decay

Type: float, Default: 0.999

Baseline decay rate. new baseline is calculated as

baseline\_decay \* baseline\_old + reward \* (1 - baseline\_

decay

ctrl\_lr

Type: float, Default: 0.00035

Controller learning rate

ctrl\_steps\_

Type: int, Default: 20

aggregate

number of steps that will be aggregated into one mini-batch for Controller

Now let’s move on to the practical application of the ENAS algorithm for the LeNet Model Space we defined in the previous section.

**TensorFlow ENAS Implementation**

Listin[g 5-11 demons](#index_split_002.html#p304)trates ENAS application using TensorFlow LeNet Model Space.

Importing modules:

***Listing 5-11.*** ENAS TensorFlow. ch5/enas/enas\_tf\_search.py

from tensorflow.keras.losses import Reduction,

SparseCategoricalCrossentropy

from tensorflow.keras.optimizers import Adam

import ch5.datasets as datasets

from nni.algorithms.nas.tensorflow import enas

from ch5.model.lenet.tf\_lenet import TfLeNetSupernet

from ch5.tf\_utils import accuracy, reward\_accuracy, get\_best\_model

Initializing LeNetSupernet:

model = TfLeNetSupernet()

Loading datasets:

dataset\_train, dataset\_valid = datasets.mnist\_dataset()

291

Chapter 5 One-ShOt neural arChiteCture SearCh

Defining loss function:

loss = SparseCategoricalCrossentropy(

from\_logits = True,

reduction = Reduction.NONE

)

Defining optimizer:

optimizer = Adam()

ENAS training params:

num\_epochs = 10

batch\_size = 256

Initializing EnasTrainer:

trainer = enas.EnasTrainer(

model,

loss = loss,

metrics = accuracy,

reward\_function = reward\_accuracy,

optimizer = optimizer,

batch\_size = batch\_size,

num\_epochs = num\_epochs,

dataset\_train = dataset\_train,

dataset\_valid = dataset\_valid,

log\_frequency = 10,

child\_steps = 10,

mutator\_steps = 30

)

Launching One-shot search:

trainer.train()

Returning best subnet:

best = get\_best\_model(trainer.mutator)

print(best)

292

Chapter 5 One-ShOt neural arChiteCture SearCh

Listin[g 5-11 r](#index_split_002.html#p304)eturns the following best model as the result of ENAS algorithm:

• conv1: 1 (Conv3×3)

• conv2: 2 (Conv5×5)

• dm: 0 (Linear256→Linear10)

**PyTorch ENAS Implementation**

Listin[g 5-12 demons](#index_split_002.html#p306)trates ENAS application using PyTorch LeNet Model Space.

Importing modules:

***Listing 5-12.*** ENAS PyTorch. ch5/enas/enas\_pt\_search.py

import torch.nn as nn

from nni.retiarii.oneshot.pytorch.enas import EnasTrainer

from torch.optim.sgd import SGD

import ch5.datasets as datasets

from ch5.model.lenet.pt\_lenet import PtLeNetSupernet

from ch5.pt\_utils import accuracy, reward\_accuracy

Initializing LeNetSupernet:

model = PtLeNetSupernet()

Loading datasets:

dataset\_train, dataset\_valid = datasets.get\_dataset("mnist")

Defining loss function:

criterion = nn.CrossEntropyLoss()

Defining optimizer:

optimizer = SGD(

model.parameters(), 0.05,

momentum = 0.9, weight\_decay = 1.0E-4

)

293

Chapter 5 One-ShOt neural arChiteCture SearCh

ENAS training params:

batch\_size = 256

log\_frequency = 50

num\_epochs = 10

ctrl\_kwargs = {"tanh\_constant": 1.1}

Initializing EnasTrainer:

trainer = EnasTrainer(

model,

loss = criterion,

metrics = accuracy,

reward\_function = reward\_accuracy,

optimizer = optimizer,

batch\_size = batch\_size,

num\_epochs = num\_epochs,

dataset = dataset\_train,

log\_frequency = log\_frequency,

ctrl\_kwargs = ctrl\_kwargs,

ctrl\_steps\_aggregate = 20

)

Launching One-shot search:

trainer.fit()

Returning best subnet:

best\_model = trainer.export()

print(best\_model)

Listin[g 5-12 r](#index_split_002.html#p306)eturns the following best model as the result of ENAS algorithm:

• conv1: 1 (Conv3×3)

• conv2: 1 (Conv3×3)

• dm: 0 (Linear256→Linear10)

294

Chapter 5 One-ShOt neural arChiteCture SearCh

ENAS is one of the first One-shot NAS algorithms that made the community rethink the whole approach to Neural Architecture Search. But ENAS may seem complicated to an inexperienced reader due to the complex internal algorithm and nontrivial tuning. In the next section, we’ll study a more elegant One-shot NAS technique.

**Differentiable Architecture Search (DARTS)**

From calculus, we know that one of the most efficient ways to find the maxima of a continuous differentiable surface is to use derivatives and gradient-based methods.

Neural networks use gradient descent based on the principle of computing derivatives.

It would also be very convenient to reduce NAS to a differentiation problem, and the DARTS algorithm does that. DARTS algorithm was proposed in the original paper

“DARTS: Differentiable Architecture Search[” (https://arxiv.org/abs/1806.09055](https://arxiv.org/abs/1806.09055)).

Using binary masks, ENAS algorithm chooses subnets from the Supernet, but this

approach is discrete. ENAS Controller jumps from one subnet to another, trying to discover the best one. DARTS algorithm makes the search space continuous; it relaxes the categorical choice of a particular operation to a softmax over all possible operations: (α ) *o* ( *x*)

*o*′( *x*) =

exp *i i*

∑ ∑ ( )

*i*

exp α *j*

*j*

This means that the DARTS algorithm creates a Supernet derived from Model

Space with sum reducing, and each choice operation is followed with *αi* parameter that specifies the weight of the operation. This makes the { *α*} parameter set trainable as Supernet weights. At the end of Supernet training, the choices with the highest *α* values are chosen as the optimal subnet operations. Figure [5-15 illus](#index_split_002.html#p309)trates this concept.

295

![](index-309_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-15.** DARTS operation relaxation*

During Supernet training using the DARTS algorithm, inefficient choices tend

to be zeroed, and the search converges to a single architecture, which is the search result. Figur[e 5-16 vis](#index_split_002.html#p310)ualizes the DARTS algorithm applied to the LeNetSupermodel. It gradually relaxes inefficient layers showing the best architecture.

296

![](index-310_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-16.** DARTS in action*

NNI 2.7 implements DARTS only for PyTorch framework using the following class:

nni.retiarii.oneshot.pytorch.DartsTrainer.

Table [5-4](#index_split_002.html#p311) shows DartsTrainer parameters.

297

Chapter 5 One-ShOt neural arChiteCture SearCh

***Table 5-4.** DartsTrainer parameters*

**Parameter**

**Description**

model

pytorch model to be trained

loss

Type: callable

loss function

metrics

Type: callable

Measures model accuracy

optimizer

Type: Optimizer

Optimizer for model training

num\_epochs

Type: int

number of epochs planned for training

dataset

Type: Dataset

training dataset

batch\_size

Type: int, Default: 64

training batch size

workers

Type: int, Default: 4

Workers for data loading

log\_frequency

Type: int, Default: None

logging step count

grad\_clip

Type: float, Default: 5.0

Gradient clipping. Set to 0 to disable

arc\_learning\_rate

Type: float, Default: 0.0001

learning rate of architecture parameters

Listin[g 5-13 im](#index_split_002.html#p311)plements DARTS algorithm using NNI.

Importing modules:

***Listing 5-13.*** DARTS PyTorch. ch5/darts/darts\_pt\_search.py

import torch

import torch.nn as nn

import ch5.datasets as datasets

from nni.retiarii.oneshot.pytorch import DartsTrainer

298

Chapter 5 One-ShOt neural arChiteCture SearCh

from ch5.model.lenet.pt\_lenet import PtLeNetSupernet

from ch5.pt\_utils import accuracy

Initializing LeNetSupernet:

model = PtLeNetSupernet()

Loading datasets:

dataset\_train, dataset\_valid = datasets.get\_dataset("mnist")

Defining loss function:

criterion = nn.CrossEntropyLoss()

Defining optimizer:

optim = torch.optim.SGD(

model.parameters(), 0.025,

momentum = 0.9, weight\_decay = 3.0E-4

)

ENAS training params:

num\_epochs = 10

batch\_size = 256

metrics = accuracy

Initializing DartsTrainer:

trainer = DartsTrainer(

model = model,

loss = criterion,

metrics = metrics,

optimizer = optim,

num\_epochs = num\_epochs,

dataset = dataset\_train,

batch\_size = batch\_size,

log\_frequency = 10,

unrolled = False

)

299

Chapter 5 One-ShOt neural arChiteCture SearCh

Launching One-shot search:

trainer.fit()

Returning best subnet:

best\_architecture = trainer.export()

print('Best architecture:', best\_architecture)

Listin[g 5-13 r](#index_split_002.html#p311)eturns the following best model as the result of DARTS algorithm:

• conv1: conv5x5->16

• conv2: conv5x5->32

• dm: 1 (Linear10)

DARTS is a clear and straightforward One-shot algorithm. It has an intuitive logic and is easy to tune. But DARTS requires more memory than ENAS because DARTS trains the whole Supernet, while ENAS trains the various subnets only. Anyway, DARTS is a good choice to implement Neural Architecture Search.

**GeneralSupernet Solving CIFAR-10**

We considered the application of One-shot algorithms on the simplest LeNet Model Space solving the trivial MNIST problem. These examples are good as entry points, but they don’t show the power of the One-shot NAS approach. In this section, we will examine a more complex Model Space for solving the CIFAR-10 problem.

Usually, One-shot NAS deals with cell-designed Supernets. As the name suggests,

a cell-designed Supernet consists of various cells. Each **cell** accepts a different number of inputs and creates a computational graph using a deep learning block operation inside. Each **block operation** is a LayerChoice of deep learning layers. Let’s build a cell-designed Supernet called **GeneralSupernet** to solve the CIFAR-10 problem.

In GeneralSupernet, we define block operation as a LayerChoice from

• SepConvBranch(3)

• NonSepConvBranch(3)

• SepConvBranch(5)

• NonSepConvBranch(3)

300

![](index-314_1.png)

![](index-314_2.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

• AvgPoolBranch

• MaxPoolBranch

The implementations of these layers are not provided here, but the reader can get details in the following source code files:

• **TensorFlow**: ch5/model/general/tf\_ops.py

• **PyTorch**: ch5/model/general/pt\_ops.py

Figur[e 5-17 depicts blo](#index_split_002.html#p314)ck operation space.

***Figure 5-17.** GeneralSupernet block operation*

Each *n* th cell accepts one required input which is transformed by block operation and *n* additional inputs. Additional inputs are not required and can be zeroed in different subnets. The normalized sum of block operation output and additional inputs forms cell output. Figur[e 5-18](#index_split_002.html#p314) demonstrates examples of cell spaces.

***Figure 5-18.** GeneralSupernet cell*

The sequence of cells forms the GeneralSupernet, and the output of each cell can be the input of the subsequent cell. After every three cells, a FactorizedReduced layer is inserted. In this section, we will use a GeneralSupernet with six cells. Figure [5-19 depicts](#index_split_002.html#p315)

GeneralSupernet architecture.

301

![](index-315_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-19.** GeneralSupernet*

302

Chapter 5 One-ShOt neural arChiteCture SearCh

Let’s calculate how many subnets GeneralSupernet has: (6) × (6×2) × (6×22) × (6×23)

× (6×24) × (6×25) = 66 × 21+2+3+4+5 ~ 1,500,000,000. Of course, it is not possible to efficiently explore this Model Space using a Multi-trial NAS approach. It is also possible to use the GeneralSupernet with 9, 12, or 24 cells. In this case, the number of subnets will become enormous.

There are a lot of predefined Supernets for One-shot NAS that are aimed at solving a specific class of problems. And GeneralSupernet we defined earlier is one of the simplest. Let’s implement GeneralSupernet and run One-shot NAS on the CIFAR-10

dataset.

**Training GeneralSupernet Using TensorFlow**

**and ENAS**

Let’s implement GeneralSupernet and find the best architecture using ENAS algorithm.

Listin[g 5-14 defines G](#index_split_002.html#p316)eneralSupernet using TensorFlow.

Importing modules:

***Listing 5-14.*** GeneralSupernet. TensorFlow. ch5/model/general/tf\_general.py from tensorflow.keras import Model, Sequential

from tensorflow.keras.layers import BatchNormalization, Conv2D, Dense,

GlobalAveragePooling2D

from nni.nas.tensorflow.mutables import InputChoice, LayerChoice,

MutableScope

from ch5.model.general.tf\_ops import build\_conv, build\_separable\_conv,

build\_avg\_pool, build\_max\_pool, FactorizedReduce

Defining Cell depicted in Figure [5-18:](#index_split_002.html#p314)

class Cell(MutableScope):

def \_\_init\_\_(self, cell\_ord, input\_num, filters):

super().\_\_init\_\_(f'cell\_{cell\_ord}')

303

Chapter 5 One-ShOt neural arChiteCture SearCh

Setting LayerChoice for block operation depicted in Figur[e 5-17](#index_split_002.html#p314): self.block\_op = LayerChoice(\[

build\_conv(filters, 3, 'conv3'),

build\_separable\_conv(filters, 3, 'sepconv3'),

build\_conv(filters, 5, 'conv5'),

build\_separable\_conv(filters, 5, 'sepconv5'),

build\_avg\_pool(filters, 'avgpool'),

build\_max\_pool(filters, 'maxpool'),

\], key = f'op\_{cell\_ord}')

Setting InputChoice for additional Cell inputs:

if input\_num > 0:

self.connections = InputChoice(

n\_candidates = input\_num,

n\_chosen = None,

key = f'con\_{cell\_ord}'

)

else:

self.connections = None

Last cell layer – BatchNormalization:

self.batch\_norm = BatchNormalization(trainable = False)

Defining call method:

def call(self, inputs):

Main input is processed by block\_op:

out = self.block\_op(inputs\[-1\])

Additional inputs are selected by self.connections and summed:

if self.connections is not None:

connection = self.connections(inputs\[:-1\])

if connection is not None:

out += connection

return self.batch\_norm(out)

304

Chapter 5 One-ShOt neural arChiteCture SearCh

Defining GeneralSupernet depicted in Figur[e 5-19](#index_split_002.html#p315):

class GeneralSupernet(Model):

def \_\_init\_\_(

self,

num\_cells = 6,

filters = 24,

num\_classes = 10

):

super().\_\_init\_\_()

self.num\_cells = num\_cells

self.stem = Sequential(\[

Conv2D(filters, kernel\_size = 3, padding = 'same', use\_bias

\= False),

BatchNormalization()

\])

Setting the positions for pool layers (FactorizedReduce):

\# num\_cells = 6 -> pool\_layers\_idx = \[3, 6\]

self.pool\_layers\_idx = \[

cell\_id

for cell\_id in range(1, num\_cells + 1) if cell\_id % 3 == 0

\]

Initializing cells and pool\_layers lists:

self.cells = \[\]

self.pool\_layers = \[\]

for cell\_ord in range(num\_cells):

if cell\_ord in self.pool\_layers\_idx:

pool\_layer = FactorizedReduce(filters)

self.pool\_layers.append(pool\_layer)

cell = Cell(cell\_ord, cell\_ord, filters)

self.cells.append(cell)

305

Chapter 5 One-ShOt neural arChiteCture SearCh

Defining final layers:

self.gap = GlobalAveragePooling2D()

self.dense = Dense(num\_classes)

Next, we define call method:

def call(self, x):

cur = self.stem(x)

prev\_outputs = \[cur\]

for cell\_id, cell in enumerate(self.cells):

Passing Cell outputs through FactorizedReduce pooling layer:

if cell\_id in self.pool\_layers\_idx:

\# Number of Pool Layer

\# 0, 1, 2, ....

pool\_ord = self.pool\_layers\_idx.index(cell\_id)

pool = self.pool\_layers\[pool\_ord\]

prev\_outputs = \[pool(tensor) for tensor in prev\_outputs\]

cur = prev\_outputs\[-1\]

cur = cell(prev\_outputs)

prev\_outputs.append(cur)

cur = self.gap(cur)

logits = self.dense(cur)

return logits

Since we defined GeneralSupernet, we can launch ENAS using the following script.

Importing modules:

***Listing 5-15.*** GeneralSupernet ENAS. TensorFlow. ch5/cifar10/enas\_tf.py from tensorflow.keras.losses import Reduction, SparseCategoricalCrossentropy

from tensorflow.keras.optimizers import SGD

import ch5.datasets as datasets

from nni.algorithms.nas.tensorflow import enas

from ch5.model.general.tf\_general import GeneralSupernet

from ch5.tf\_utils import accuracy, reward\_accuracy, get\_best\_model

306

Chapter 5 One-ShOt neural arChiteCture SearCh

Initializing GeneralSupernet:

model = GeneralSupernet()

Loading datasets:

dataset\_train, dataset\_valid = datasets.cifar10\_dataset()

Declaring loss function:

loss = SparseCategoricalCrossentropy(

from\_logits = True,

reduction = Reduction.NONE

)

Declaring optimizer:

optimizer = SGD(learning\_rate = 0.05, momentum = 0.9)

Setting ENAS trainer parameters:

metrics = accuracy

reward\_function = reward\_accuracy

batch\_size = 256

num\_epochs = 100

Initializing EnasTrainer:

trainer = enas.EnasTrainer(

model,

loss = loss,

metrics = metrics,

reward\_function = reward\_function,

optimizer = optimizer,

batch\_size = batch\_size,

num\_epochs = num\_epochs,

dataset\_train = dataset\_train,

dataset\_valid = dataset\_valid

)

307

Chapter 5 One-ShOt neural arChiteCture SearCh

Launching training:

trainer.train()

Displaying results:

best = get\_best\_model(trainer.mutator)

print(best)

**Note** Duration ~ 6 hours on intel Core i7 with CuDa (GeForce GtX 1050)

After the search was completed, the following report was returned:

• op\_layer\_0: 3 SepConvBranch(5)

• op\_layer\_1: 3 SepConvBranch(5)

• op\_layer\_2: 1 SepConvBranch(3)

• op\_layer\_3: 4 NonSepConvBranch(3)

• op\_layer\_4: 1 SepConvBranch(3)

• op\_layer\_5: 1 SepConvBranch(3)

• con\_layer\_1: 0 Additional input from Cell0

• con\_layer\_2: 0 Additional input from Cell0

• con\_layer\_3: None No additional inputs

• con\_layer\_4: \[0, 2, 3\] Additional inputs from: Cell0,

Cell2, Cell3

• con\_layer\_5: 3 Additional input from Cell3

Figur[e 5-20 vis](#index_split_003.html#p322)ualizes the result returned by ENAS.

308

![](index-322_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-20.** ENAS GeneralSupernet best architecture*

As see in Figure [5-20, the b](#index_split_003.html#p322)est architecture does not use pooling operations, AvgPoolBranch and MaxPoolBranch, and this makes sense because GeneralSupernet has built-in FactorizedReduced layers.

309

Chapter 5 One-ShOt neural arChiteCture SearCh

**Training GeneralSupernet Using PyTorch and DARTS**

Let’s implement GeneralSupernet and find the best architecture using DARTS algorithm.

First, we need to define GeneralSupernet using PyTorch.

Importing modules:

***Listing 5-16.*** GeneralSupernet. PyTorch. ch5/model/general/pt\_general.py from typing import OrderedDict

import torch.nn as nn

from nni.retiarii.nn.pytorch import LayerChoice, InputChoice

from ch5.model.general.pt\_ops import ConvBranch, PoolBranch, FactorizedReduce

Defining Cell depicted in Figure [5-18:](#index_split_002.html#p314)

class Cell(nn.Module):

def \_\_init\_\_(self, cell\_ord, input\_num, in\_f, out\_f):

super().\_\_init\_\_()

Setting LayerChoice for block operation depicted in Figur[e 5-17](#index_split_002.html#p314): self.block\_op = LayerChoice(OrderedDict(\[

('SepConvBranch(3)', ConvBranch(in\_f, out\_f, 3, 1, 1, False)),

('NonSepConvBranch(3)', ConvBranch(in\_f, out\_f, 3, 1, 1, True)),

('SepConvBranch(5)', ConvBranch(in\_f, out\_f, 5, 1, 2, False)),

('NonSepConvBranch(3)', ConvBranch(in\_f, out\_f, 5, 1, 2, True)),

('AvgPoolBranch', PoolBranch('avg', in\_f, out\_f, 3, 1, 1)),

('MaxPoolBranch', PoolBranch('max', in\_f, out\_f, 3, 1, 1))

\]), label = f'op\_{cell\_ord}')

Setting InputChoice for additional Cell inputs:

if input\_num > 0:

self.connections = InputChoice(

n\_candidates = input\_num, n\_chosen = None,

label = f'con\_{cell\_ord}'

)

else:

self.connections = None

310

Chapter 5 One-ShOt neural arChiteCture SearCh

Last cell layer – BatchNormalization:

self.batch\_norm = nn.BatchNorm2d(out\_f, affine = False)

Defining forward method:

def forward(self, inputs):

Main input is processed by block\_op:

out = self.block\_op(inputs\[-1\])

Additional inputs are selected by self.connections and summed:

if self.connections is not None:

connection = self.connections(inputs\[:-1\])

if connection is not None:

out = out + connection

return self.batch\_norm(out)

Defining GeneralSupernet depicted in Figur[e 5-19](#index_split_002.html#p315):

class GeneralSupernet(nn.Module):

def \_\_init\_\_(

self,

num\_cells = 6,

out\_f = 24,

in\_channels = 3,

num\_classes = 10

):

super().\_\_init\_\_()

self.num\_cells = num\_cells

\# Stem layer

self.stem = nn.Sequential(

nn.Conv2d(in\_channels, out\_f, 3, 1, 1, bias = False),

nn.BatchNorm2d(out\_f)

)

311

Chapter 5 One-ShOt neural arChiteCture SearCh

Setting the positions for pool layers (FactorizedReduce):

self.pool\_layers\_idx = \[

cell\_id

for cell\_id in range(1, num\_cells + 1) if cell\_id % 3 == 0

\]

Initializing cells and pool\_layers lists:

self.cells = nn.ModuleList()

self.pool\_layers = nn.ModuleList()

\# Initializing Cells and Pool Layers

for cell\_ord in range(num\_cells):

if cell\_ord in self.pool\_layers\_idx:

pool\_layer = FactorizedReduce(out\_f, out\_f)

self.pool\_layers.append(pool\_layer)

cell = Cell(cell\_ord, cell\_ord, out\_f, out\_f)

self.cells.append(cell)

Defining final layers:

self.gap = nn.AdaptiveAvgPool2d(1)

self.dense = nn.Linear(out\_f, num\_classes)

Next, we define forward method:

def forward(self, x):

bs = x.size(0)

cur = self.stem(x)

\# Constructing Calculation Graph

cells = \[cur\]

for cell\_id in range(self.num\_cells):

cur = self.cells\[cell\_id\](cells)

cells.append(cur)

312

Chapter 5 One-ShOt neural arChiteCture SearCh

Passing Cell outputs through FactorizedReduce pooling layer:

\# If pool layer is added

if cell\_id in self.pool\_layers\_idx:

\# Number of Pool Layer

\# 0, 1, 2, ...

pool\_ord = self.pool\_layers\_idx.index(cell\_id)

\# Adding Pool Layer to all input cells

for i, cell in enumerate(cells):

cells\[i\] = self.pool\_layers\[pool\_ord\](cell)

cur = cells\[-1\]

cur = self.gap(cur).view(bs, -1)

logits = self.dense(cur)

return logits

Since we defined GeneralSupernet, we can launch DARTS using Listing [5-17.](#index_split_003.html#p326)

Importing modules:

***Listing 5-17.*** GeneralSupernet DARTS. PyTorch. ch5/cifar10/darts\_pt.py import torch

import torch.nn as nn

import ch5.datasets as datasets

from nni.retiarii.oneshot.pytorch import DartsTrainer

from ch5.model.general.pt\_general import GeneralSupernet

from ch5.pt\_utils import accuracy

Initializing GeneralSupernet:

model = GeneralSupernet()

Loading datasets:

dataset\_train, dataset\_valid = datasets.get\_dataset("cifar10")

Declaring loss function:

criterion = nn.CrossEntropyLoss()

313

Chapter 5 One-ShOt neural arChiteCture SearCh

Declaring optimizer:

optim = torch.optim.SGD(

model.parameters(), 0.025,

momentum = 0.9, weight\_decay = 3.0E-4

)

Setting DARTS trainer parameters:

num\_epochs = 100

batch\_size = 128

accuracy\_metrics = accuracy

Initializing DartsTrainer:

trainer = DartsTrainer(

model = model,

loss = criterion,

metrics = accuracy\_metrics,

optimizer = optim,

num\_epochs = num\_epochs,

dataset = dataset\_train,

batch\_size = batch\_size,

log\_frequency = 10,

unrolled = False

)

Launching training:

trainer.fit()

314

Chapter 5 One-ShOt neural arChiteCture SearCh

Displaying results:

best\_architecture = trainer.export()

print('Best architecture:', best\_architecture)

**Note** Duration ~ 4 hours on intel Core i7 with CuDa (GeForce GtX 1050)

After the search was completed, the following report was returned:

• op\_layer\_0: SepConvBranch(3)

• op\_layer\_1: SepConvBranch(5)

• op\_layer\_2: SepConvBranch(5)

• op\_layer\_3: SepConvBranch(5)

• op\_layer\_4: SepConvBranch(5)

• op\_layer\_5: MaxPoolBranch

• con\_layer\_1: 0 Additional input from Cell0

• con\_layer\_2: 0 Additional input from Cell0

• con\_layer\_3: 0 Additional input from Cell0

• con\_layer\_4: 2 Additional input from Cell2

• con\_layer\_5: 4 Additional input from Cell4

Figur[e 5-21 vis](#index_split_003.html#p329)ualizes the result returned by DARTS.

315

![](index-329_1.png)

Chapter 5 One-ShOt neural arChiteCture SearCh

***Figure 5-21.** DARTS GeneralSupernet best architecture*

316

Chapter 5 One-ShOt neural arChiteCture SearCh

The architectures obtained using ENAS (Figur[e 5-20) and D](#index_split_003.html#p322)ARTS (Figure-21) are similar. They tend to use the SepConvBranch(5) operation and share Cell0 output.

ENAS best architecture and DARTS best architecture achieve 91.2% and 92.8% accuracy, respectively. But we can further improve the accuracy if we increase the number of cells (num\_cells) in the GeneralSupernet. This will make the search longer, but it will result in a more accurate target architecture. The beautiful thing is that we can use the same GeneralSupernet and One-shot algorithm for any pattern recognition problem. This gives us a universal approach to solving typical deep learning problems. Absolutely Oneshot NAS is one of the most significant achievements of automated deep learning.

**HPO vs. Multi-trial NAS vs. One-Shot NAS**

And so, at the moment, we have three different approaches to optimize and construct deep learning models: HPO, Multi-trial NAS, and One-shot NAS. And a fair question may arise: which method is better to choose? But this question does not have a clear answer.

Each approach is better suited for a specific task.

• **HPO** deals with black-box optimization and is suitable for selecting

optimization algorithms, training batch size, and tuning the

predesigned model. HPO results can be visualized and easily

analyzed. HPO can be a good starting point to dive into a completely

new problem or a good finishing point when the final tuning is

performed.

• **Multi-trial NAS** is only concerned with finding the optimal

architecture. Despite its durability, Multi-trial NAS is more accurate

than One-shot NAS. Multi-trial NAS results are much easier to

interpret because this approach provides metrics for each tried

architecture.

• **One-shot NAS** is well suited for finding complex architectures for

very tough tasks. One-shot NAS is good at finding optimal subnets in

Model Space with millions and billions of elements. It is fast, but it is

hard to interpret because you get only the best subnet, and you don’t

know any additional information about another possible solution.

317

Chapter 5 One-ShOt neural arChiteCture SearCh

Table [5-5](#index_split_003.html#p331) shows a comparison of different approaches, where

• ✓✓✓: Well suited

• ✓✓: Suited

• ✓: Poorly suited

***Table 5-5.** AutoDL approaches comparison*

**HPO**

**Multi-trial One-shot**

**NAS**

**NAS**

ease of setup

✓✓✓

✓✓

✓

Search flexibility

✓✓✓

✓✓

✓

interpretability of results

✓✓✓

✓✓

✓

Designing the neural network search space

✓

✓✓✓

✓✓

Search for small neural networks for simple tasks

✓

✓✓✓

✓

Search for complex architectures for challenging tasks

✓

✓✓

✓✓✓

Optimization of the predesigned architecture for a specific

✓✓✓

✓✓

✓

dataset

And here, we again face the problem that there is no unique approach for solving any situation, and the No Free Lunch theorem applies here as well. But understanding how each algorithm acts will help you make the right choice for solving a particular problem.

**Summary**

One-shot NAS is a very promising area of study. It allows you to find neural network solutions in a reasonable time. Currently, One-shot algorithms can discover completely new architectural keys to solve the most complex problems. This field is developing rapidly and will be a handy tool in any researcher’s toolkit. In this chapter, we introduced the basic concepts of One-shot NAS and mastered using two of its algorithms: ENAS

and DARTS. This can be a good starting point for putting One-shot NAS into practice. In the next chapter, we will consider the important problem of model compression, which allows you to eliminate unnecessary neural network elements without losing its accuracy.

318

**CHAPTER 6**

**Model Pruning**

Deep learning models have reached significant success in many real-life problems. A lot of devices use neural networks to perform everyday tasks. However, complex neural networks are computationally expensive. And not all devices have GPU processors

to run deep learning models. Therefore, it would be helpful to perform model

compression methods to reduce the model size and accelerate model performance

without losing accuracy significantly. One of the main model compression techniques is model pruning. Pruning optimizes the model by eliminating some model weights.

It can eliminate a significant amount of model weights with no negligible damage to model performance. A pruned model is lighter and faster. Pruning is a straightforward approach that can give nice model speedup results.

NNI provides a toolkit to help users to execute model pruning algorithms. NNI 2.7

version (which is used in this book) supports pruning for the PyTorch framework only.

This chapter will study several pruning algorithms and learn how to apply them in practice.

**What Is Model Pruning?**

Complex neural networks have a lot of layers and many weights. ResNet, DenseNet, and VGGNet take up tens of megabytes to store their weights. Developers often use these architectures to solve many practical problems. But the chosen architecture is often too redundant for the problem being solved, and it contains a lot of extra weights and even extra layers. In practice, you can remove excess weights from the model, which will significantly speed up calculations in the neural network. Sometimes, deep learning models perfectly fit the problem, and they do not have explicit redundancy. Still, they are too computationally heavy to be deployed to the special device they need to act in. In such cases, developers may sacrifice the model accuracy for acceleration.

319

© Ivan Gridin 2022

I. Gridin, *Automated Deep Learning Using Neural Network Intelligence*,

[https://doi.org/10.1007/978-1-4842-8149-9\_6](https://doi.org/10.1007/978-1-4842-8149-9_6#DOI)

Chapter 6 Model pruning

Let’s describe how the pruning algorithm acts:

1\. We take a ready-to-use pre-trained deep learning model we want

to prune.

2\. Pruning algorithm eliminates (prunes) several weights in the

neural network. By eliminating, we mean that the algorithm

zeroes these weights. Zeroing the weights significantly speeds

up calculations since multiplying by 0 is always 0, and there is

no need to do complex calculations. Usually, candidates for

elimination are already close to zero, so their zeroing should not

seriously affect the model’s performance.

3\. Pruned model is retrained (fine-tuned) on the same dataset as the

original model, but zeroed weights no longer change their values

and remain zero all the time. During retraining, active weights

try to take over the functions of the removed neurons to continue

solving the problem successfully.

Figur[e 6-1 illus](#index_split_003.html#p334)trates the pruning algorithm.

320

![](index-334_1.png)

Chapter 6 Model pruning

***Figure 6-1.** Pruning algorithm application*

321

Chapter 6 Model pruning

Pruning is a great technique, but sometimes, it degrades the model. It is not always possible to remove weights without compromising the model’s accuracy in complex

neural networks. However, model accuracy degradation can be minimal, and we’ll see further that it is possible to compress a model by 80% with almost no accuracy decrease.

**Note** term

**fine-tuning** means retraining technique that trains the unpruned

weights from their final trained values. in this chapter, we will use the terms

**fine- tuning** and **retraining** interchangeably.

**LeNet Model Pruning**

The best way to understand the concept of model pruning is to put it into practice. Let’s get back to the well-known LeNet model and the classic MNIST problem. The LeNet

model design is shown in Listin[g 6-1.](#index_split_003.html#p335)

(Full code is provided in the corresponding file: ch6/model/pt\_lenet.py.)

PtLeNetModel provides familiar model design:

***Listing 6-1.*** LeNet model

class **PtLeNetModel**(nn.Module):

def **\_\_init\_\_**(self, fs = 16, ks = 5):

super(PtLeNetModel, self).\_\_init\_\_()

self.conv1 = nn.Conv2d(1, fs, ks)

self.conv2 = nn.Conv2d(fs, fs \* 2, ks)

self.conv3 = nn.Conv2d(fs \* 2, fs \* 2, ks)

self.fc1 = nn.Linear(288, 64)

self.fc2 = nn.Linear(64, 32)

self.fc3 = nn.Linear(32, 10)

def **forward**(self, x):

x = F.relu(self.conv1(x))

x = F.relu(self.conv2(x))

x = F.max\_pool2d(x, 2, 2)

322

Chapter 6 Model pruning

x = F.relu(self.conv3(x))

x = F.max\_pool2d(x, 2, 2)

x = torch.flatten(x, start\_dim = 1)

x = torch.relu(self.fc1(x))

x = torch.relu(self.fc2(x))

x = torch.relu(self.fc3(x))

return F.log\_softmax(x, dim = 1)

Next, we add two helper methods that we will need in the future: count\_total\_

weights and count\_total\_weights. count\_nonzero\_weights is a helper method that

counts the number of zeros in the neural network’s weights, and count\_total\_weights counts the total number of neural network weights.

def **count\_nonzero\_weights**(self):

counter = 0

for params in list(self.parameters()):

counter += torch.count\_nonzero(params).item()

return counter

def **count\_total\_weights**(self):

counter = 0

for params in list(self.parameters()):

counter += torch.numel(params)

return counter

The trained PtLeNetModel is saved in the following file: ch6/data/lenet.pth. It shows 0.991 accuracy on the test MNIST dataset. Listing [6-2](#index_split_003.html#p336) demonstrates how original pre-trained PtLeNetModel can be pruned.

We import necessary modules:

***Listing 6-2.*** LeNet model pruning. ch6/prune/prune.py

import os

import random

import matplotlib.pyplot as plt

import torch

from nni.algorithms.compression.v2.pytorch.pruning import LevelPruner

323

Chapter 6 Model pruning

from ch6.datasets import mnist\_dataset

from ch6.model.pt\_lenet import PtLeNetModel

CUR\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_))

Making script reproducible:

\# Making script reproducible

random.seed(1)

torch.manual\_seed(1)

Loading pre-trained PtLeNetModel:

model = PtLeNetModel()

path = f'{CUR\_DIR}/../data/lenet.pth'

model.load\_state\_dict(torch.load(path))

Loading MNIST dataset:

train\_ds, test\_ds = mnist\_dataset()

Storing accuracy of original model:

original\_acc = model.test\_model(test\_ds)

Storing nonzero weights of original model:

original\_nzw = model.count\_nonzero\_weights()

Next, we are pruning original model with one-shot LevelPruner (pruning algorithm internals will be explained in the next section):

\# Pruning Config

prune\_config = \[{

'sparsity': .8,

'op\_types': \['default'\],

}\]

\# LevelPruner

pruner = LevelPruner(model, prune\_config)

324

Chapter 6 Model pruning

Compressing the original model:

model\_pruned, \_ = pruner.compress()

Fine-tuning (retraining compressed model):

epochs = 10

acc\_list = \[\]

for epoch in range(1, epochs + 1):

model\_pruned.train\_model(epochs = 1, train\_dataset = train\_ds)

acc = model\_pruned.test\_model(test\_dataset = test\_ds)

acc\_list.append(acc)

print(f'Pruned: Epoch {epoch}. Accuracy: {acc}.')

Since the compressed model is fine-tuned, let’s visualize retraining progress:

pruned\_nzw = model\_pruned.count\_nonzero\_weights()

plt.title(

'Fine-tuning\\n'

f'Original Non-zero weights number: {original\_nzw}\\n'

f'Pruned Non-zero weights number: {pruned\_nzw}')

plt.axhline(y = original\_acc, c = "red",

label = 'Original model accuracy')

plt.plot(acc\_list, label = 'Pruned model accuracy')

plt.xlabel('Retraining Epochs')

plt.ylabel('Accuracy')

plt.legend()

plt.show()

Visualization result is shown in Figure [6-2](#index_split_003.html#p339).

325

![](index-339_1.png)

Chapter 6 Model pruning

***Figure 6-2.** LeNet retraining progress*

Figur[e 6-2 illus](#index_split_003.html#p339)trates fine-tuning of the compressed model. Original trained LeNet model has 59,786 nonzero weights, and compressed LeNetModel has 12,107 nonzero

weights only. At the beginning of the retraining, the compressed model is less accurate than the original model. But after 10 training epochs, the compressed model achieves the same accuracy as the original model, having only 12,107 active weights out of 59,780. Obviously, the original LeNet model was redundant and could be replaced by pruned one.

Finally, let’s save the pruned model for future usage:

model\_path = f'{CUR\_DIR}/../data/lenet\_pruned.pth'

mask\_path = f'{CUR\_DIR}/../data/mask.pth'

pruner.export\_model(

model\_path = model\_path,

mask\_path = mask\_path

)

326

Chapter 6 Model pruning

NNI provides a special wrapper that allows loading pruned models nni.

compression.pytorch.ModelSpeedup and use them after. In Listin[g 6-3, w](#index_split_003.html#p340)e load pruned LeNet model and analyze its characteristics.

(Please install the following package to run this script: torchsummary.)

Importing modules:

***Listing 6-3.*** Pruned LeNet model usage. ch6/prune/analyze\_pruned.py import os

import torch

from nni.compression.pytorch import ModelSpeedup

from torchsummary import summary

from ch6.model.pt\_lenet import PtLeNetModel

CUR\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_))

Loading pruned model using ModelSpeedup wrapper:

dummy\_input = torch.randn((500, 1, 28, 28))

model\_path = f'{CUR\_DIR}/../data/lenet\_pruned.pth'

mask\_path = f'{CUR\_DIR}/../data/mask.pth'

model\_pruned = PtLeNetModel()

model\_pruned.load\_state\_dict(torch.load(model\_path))

speedup = ModelSpeedup(model\_pruned, dummy\_input, mask\_path)

speedup.speedup\_model()

model\_pruned.eval()

Let’s check the accuracy of the pruned model:

acc = model\_pruned.test\_model()

print(acc)

The pruned model returns 0.9916 accuracy, the same as the original unpruned

model. Also, the pruned model actually shrinks its layers deleting unnecessary weights.

The pruned model is less than the original one, and let’s examine the difference between them:

\# Loading Original Model

model\_original = PtLeNetModel()

model\_path = f'{CUR\_DIR}/../data/lenet.pth'

327

Chapter 6 Model pruning

model\_original.load\_state\_dict(torch.load(model\_path))

\# Displaying summary of Original and Pruned models

print('==== ORIGINAL MODEL =====')

summary(model\_original, (1, 28, 28))

print('=========================')

print('==== PRUNED MODEL =====')

summary(model\_pruned, (1, 28, 28))

print('=========================')

Table [6-1](#index_split_003.html#p341) compares original model and pruned one.

***Table 6-1.** Original and pruned model comparison*

**Layer**

**Original**

**Original**

**Pruned**

**Pruned**

**Output Shape**

**Size**

**Output Shape**

**Size**

Conv2d-1

\[16,24,24\]

416

**\[14,24,24\]**

364

Conv2d-2

\[32,20,20\]

12,832

\[32,20,20\]

11,232

Conv2d-3

\[32,6,6\]

25,632

**\[30,6,6\]**

24,030

Linear-4

\[64\]

18,496

**\[61\]**

16,531

Linear-5

\[32\]

2,080

**\[25\]**

1,550

Linear-6

\[10\]

330

\[10\]

260

As shown in Ta[ble 6-1, pr](#index_split_003.html#p341)uned model shrinks Conv2d-1, Conv2d-3, Linear-4, and Linear-5 layers. And this is the primary goal of the pruning algorithm, which eliminates redundancy from the neural network. The earlier example illustrates how we can prune a pre-trained model using NNI. Let’s move forward and study pruning algorithms in more detail.

328

![](index-342_1.png)

Chapter 6 Model pruning

**One-Shot Pruners**

One-shot pruning algorithms prune weights only once based on a specific metric.

Usually, pruned weights are close to zero, and pruner suggests that their removal will not impact the model’s accuracy. One-shot pruners act the following way:

• Pruner accepts a model and selects active weights and the weights to

be pruned. As a result, the pruner returns a model and a binary mask,

where 1 means active weight and 0 means weight to be pruned.

• Original model is speeded up by pruning redundant weights resulting

a compressed model.

• Fine-tuning algorithm retrains the compressed model to adjust its

weights.

This pruner flow algorithm is depicted in Figure [6-3](#index_split_003.html#p342).

***Figure 6-3.** One-shot pruning*

We can define the main steps to implement one-shot pruning algorithms using NNI

the following way:

1\. Load a pre-trained model

2\. Initialize pruner

3\. Compress original model

4\. Retrain compressed model

329

Chapter 6 Model pruning

5\. Save compressed model

6\. Load and speed up compressed model

**Step 1**. Model loading is a native PyTorch operation:

model = SomeModel()

model.load\_state\_dict(torch.load(model\_path))

**Step 2**. To initialize the pruner, we must specify the pruner configuration (we will study the pruner configuration in the next section). Here is an example of pruner initialization: prune\_config = \[{

'sparsity': .8,

'op\_types': \['default'\],

}\]

pruner = LevelPruner(model, prune\_config)

**Step 3**. Pruner compresses original model applying its logic to reduce model weights: model\_pruned, mask = pruner.compress()

**Step 4**. Compressed model is being retrained according to the same training algorithm as the original one:

for epoch in range(1, epochs + 1):

pruner.update\_epoch(epoch)

train(model, dataset, optimizer, criterion)

**Step 5**. Compressed model is stored using pruner.export\_model method:

pruner.export\_model(model\_path = model\_path, mask\_path = mask\_path)

**Step 6**. Saved model is loaded and wrapped by nni.compression.pytorch.

ModelSpeedup class:

\# dummy input tensor

dummy\_input = torch.randn((500, 1, 28, 28))

model\_pruned = SomeModel()

model\_pruned.load\_state\_dict(torch.load(model\_path))

speedup = ModelSpeedup(model\_pruned, dummy\_input, mask\_path)

speedup.speedup\_model()

330

Chapter 6 Model pruning

And that’s it. The compressed model is ready to use! Let’s create a helper script that will apply steps 2–6 we defined earlier. Listin[g 6-4 a](#index_split_003.html#p344)pplies a pruning algorithm and returns a compressed model.

Importing modules:

***Listing 6-4.*** Pruning implementation. ch6/algos/utils.py

import copy

import os

import torch

from nni.compression.pytorch import ModelSpeedup

from torchsummary import summary

CUR\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_))

oneshot\_prune method accepts the following parameters:

• model\_original: Pre-trained original model

• pruner\_cls: Pruner class

• pruner\_config: Pruner configuration

• train\_ds: Train dataset

• epochs: Number of training epochs

• model\_input\_shape: Shape of model input

def oneshot\_prune(

model\_original,

pruner\_cls,

pruner\_config,

train\_ds,

epochs = 10,

model\_input\_shape = (1, 1, 28, 28)

):

pruner\_name = pruner\_cls.\_\_name\_\_

model = copy.deepcopy(model\_original)

331

Chapter 6 Model pruning

**Step 2**. Initializing pruner:

pruner = pruner\_cls(model, pruner\_config)

**Step 3**. Compressing original model:

model\_pruned, mask = pruner.compress()

**Step 4**. Retraining compressed model:

for epoch in range(1, epochs + 1):

model\_pruned.train\_model(

epochs = 1,

train\_dataset = train\_ds

)

**Step 5**. Saving compressed model:

model\_path = f'{CUR\_DIR}/../data/{pruner\_name}\_pruned.pth'

mask\_path = f'{CUR\_DIR}/../data/{pruner\_name}\_mask.pth'

pruner.export\_model(

model\_path = model\_path,

mask\_path = mask\_path

)

**Step 6**. Loading and speeding up compressed model:

dummy\_input = torch.randn(model\_input\_shape)

model\_pruned = model\_original.\_\_class\_\_()

model\_pruned.load\_state\_dict(torch.load(model\_path))

speedup = ModelSpeedup(model\_pruned, dummy\_input, mask\_path)

speedup.speedup\_model()

model\_pruned.eval()

return model\_pruned

Fine. Since we know how to apply one-shot pruning algorithms, let’s go further and study some of them.

332

Chapter 6 Model pruning

**Pruner Configuration**

Each pruner accepts configuration, which specifies its internal logic. Pruner

configuration is a List of Dict entries, and each entry specifies a pruning strategy applied to a specified layer set. Ta[ble 6-2 des](#index_split_003.html#p346)cribes pruner configuration parameters.

***Table 6-2.** Pruner configuration*

**Key**

**Description**

sparsity Specifies the sparsity for each layer in this configuration entry to be compressed. if sparsity = 0.8, then 80% of layer weights will be pruned, and 20% will be left

active

op\_types Specifies what types of operations to compress. 'default' means following the algorithm’s default setting. all supported module types for pytorch are defined package file nni/compression/pytorch/default\_layers.py:

'Conv1d', 'Conv2d', 'Conv3d', 'ConvTranspose1d',

'ConvTranspose2d', 'ConvTranspose3d', 'Linear', 'Bilinear',

'PReLU', 'Embedding', 'EmbeddingBag'

op\_names Specifies names of operations to be compressed. if this field is omitted, operations will not be filtered by it

op\_

operation partial names to be compressed. if op\_partial\_names = 'fc\_', then all

partial\_ layers with the following mask 'fc\_\*' will be pruned

names

exclude

default is False. if this field is true, it means the operations with specified types and names will be excluded from the compression

Here is an example of the pruning configuration of a one-shot pruner applied to the LeNet model:

prune\_config = \[

{

'sparsity': .8,

'op\_types': \['Conv2d'\],

},

333

Chapter 6 Model pruning

{

'sparsity': .6,

'op\_types': \['Linear'\],

},

{

'op\_names': \['fc3'\],

'exclude': True

}

\]

If you don’t want to specify a special pruning strategy for each layer type, then you can use the following configuration:

prune\_config = \[

{

'sparsity': .8,

'op\_types': \['default'\]

}

\]

**Level Pruner**

Level pruner is a straightforward one-shot pruner. Sparsity level means prune ratio, that is, sparsity=0.7 means that 70% of model weight parameters will be pruned. Level pruner sorts the weights in the specified layer by their absolute values. And then mask to zero the smallest magnitude weights until the desired sparsity level is reached.

Level pruner is applied the following way:

from nni.algorithms.compression.v2.pytorch.pruning import LevelPruner

**prune\_config** = \[{

'sparsity': .8,

'op\_types': \['default'\],

}\]

pruner = **LevelPruner**(model, prune\_config)

model\_pruned, mask = pruner.compress()

334

Chapter 6 Model pruning

Let’s apply LevelPruner to prune the LeNet model using Listin[g 6-5](#index_split_003.html#p348).

Importing modules:

***Listing 6-5.*** LevelPruner. ch6/algos/one\_shot/level\_pruner.py

from nni.algorithms.compression.v2.pytorch.pruning import LevelPruner

from ch6.algos.utils import model\_comparison, oneshot\_prune, visualize\_mask

from ch6.datasets import mnist\_dataset

from ch6.model.pt\_lenet import PtLeNetModel

Loading pre-trained model and MNIST dataset:

original = PtLeNetModel.load\_model()

train\_ds, test\_ds = mnist\_dataset()

We will prune Conv2d layers with 0.8 sparsity and Linear layers with 0.6 sparsity.

Also, we will exclude the final classifier linear layer fc3 from pruning.

prune\_config = \[

{

'sparsity': .8,

'op\_types': \['Conv2d'\],

},

{

'sparsity': .6,

'op\_types': \['Linear'\],

},

{

'op\_names': \['fc3'\],

'exclude': True

}

\]

Defining pruner:

pruner\_cls = LevelPruner

335

![](index-349_1.png)

Chapter 6 Model pruning

Compressing original model using LevelPruner:

compressed, mask = oneshot\_prune(

original,

pruner\_cls,

prune\_config,

train\_ds,

epochs = 10

)

Visualizing prune mask:

visualize\_mask(mask)

Figur[e 6-4 sho](#index_split_003.html#p349)ws the mask of a pruned model. We see that the mask leaves 40%

active weights for linear layers and 20% active weights for convolutional layers.

***Figure 6-4.** LevelPruner active weights*

Comparing original model and compressed one:

model\_comparison(original, compressed, test\_ds, (1, 28, 28))

The original model has 0.991 accuracy, and the compressed one has the same 0.991

accuracy. Ta[ble 6-3 com](#index_split_003.html#p350)pares the architectures of original and compressed models.

336

Chapter 6 Model pruning

***Table 6-3.** Original and level pruned model comparison*

**Layer**

**Original Output**

**Original**

**Pruned Output**

**Pruned**

**Shape**

**Size**

**Shape**

**Size**

Conv2d-1

\[16,24,24\]

416

**\[14,24,24\]**

364

Conv2d-2

\[32,20,20\]

12,832

\[32,20,20\]

11,232

Conv2d-3

\[32,6,6\]

25,632

**\[30,6,6\]**

24,030

Linear-4

\[64\]

18,496

\[64\]

17,344

Linear-5

\[32\]

2,080

\[32\]

2,080

Linear-6

\[10\]

330

\[10\]

330

**Total**

59,786

**55,380**

Level pruner compressed the original LeNet model without decreasing its accuracy.

**FPGM Pruner**

FPGM (Filter Pruning via Geometric Median) Pruner is a one-shot pruner that prunes filters with the smallest geometric median. For more details, please refer to the original paper “Filter Pruning via Geometric Median for Deep Convolutional Neural Networks Acceleration” ([https://arxiv.org/pdf/1811.00250.pdf).](https://arxiv.org/pdf/1811.00250.pdf)

FPGM Pruner supports Conv2d, Linear as layers for pruning operation. FPGM

Pruner is applied the following way:

from nni.algorithms.compression.v2.pytorch.pruning import FPGMPruner

**prune\_config** = \[{

'sparsity': .8,

'op\_types': \['Conv2d'\],

}\]

pruner = **FPGMPruner**(model, prune\_config)

model\_pruned, mask = pruner.compress()

337

Chapter 6 Model pruning

Here is an example of FPGMPruner application.

Importing modules:

***Listing 6-6.*** FPGMPruner. ch6/algos/one\_shot/fpgm\_pruner.py

from nni.algorithms.compression.v2.pytorch.pruning import FPGMPruner

from ch6.algos.utils import oneshot\_prune, model\_comparison, visualize\_mask

from ch6.datasets import mnist\_dataset

from ch6.model.pt\_lenet import PtLeNetModel

Loading pre-trained model and MNIST dataset:

original = PtLeNetModel.load\_model()

train\_ds, test\_ds = mnist\_dataset()

Pruning convolutional layers of original model using FPGMPruner with 0.5 sparsity: compressed, mask = oneshot\_prune(

original,

FPGMPruner,

\[{

'sparsity': .5,

'op\_types': \['Conv2d'\],

}\],

train\_ds

)

Visualizing prune mask:

visualize\_mask(mask)

Figur[e 6-5 sho](#index_split_003.html#p352)ws the mask of the compressed model. We see that the mask leaves 50% active weights for Conv2d layers.

338

![](index-352_1.png)

Chapter 6 Model pruning

***Figure 6-5.** FPGMPruner active weights*

Comparing original model and compressed one:

model\_comparison(original, compressed, test\_ds, (1, 28, 28))

Original model has 0.991 accuracy, while the compressed one has close accuracy

0.9894. Table [6-4](#index_split_003.html#p352) compares the architectures of original and compressed models.

***Table 6-4.** Original and FPGM pruned model comparison*

**Layer**

**Original**

**Original**

**Pruned**

**Pruned**

**Output Shape**

**Size**

**Output Shape**

**Size**

Conv2d-1

\[16,24,24\]

416

**\[8,24,24\]**

**208**

Conv2d-2

\[32,20,20\]

12,832

**\[16,20,20\]**

**3,216**

Conv2d-3

\[32,6,6\]

25,632

**\[16,6,6\]**

**6,416**

Linear-4

\[64\]

18,496

\[64\]

9,280

Linear-5

\[32\]

2,080

\[32\]

2,080

Linear-6

\[10\]

330

\[10\]

330

**Total**

59,786

**21,530**

Table [6-4](#index_split_003.html#p352) shows that FPGMPruner compressed the original model very heavily with almost no loss of accuracy.

339

Chapter 6 Model pruning

**L1Norm and L2Norm Pruners**

L1Norm Pruner and L2Norm Pruner are one-shot pruners that prune layers according to *L1-norm* and *L2-norm*, respectively. For more details, please refer to the original paper

“Pruning Filters for Efficient ConvNets[” (https://arxiv.org/pdf/1608.08710.pdf](https://arxiv.org/pdf/1608.08710.pdf)).

L1Norm and L2Norm pruners support Conv2d, Linear as a layer for pruning

operation. L1NormPruner and L2NormPruner are applied the following way:

from nni.algorithms.compression.v2.pytorch.pruning import L1NormPruner,

L2NormPruner

**prune\_config** = \[{

'sparsity': .8,

'op\_types': \['Conv2d'\],

}\]

pruner = **L1NormPruner**(model, prune\_config)

\# pruner = **L2NormPruner**(model, prune\_config)

model\_pruned, mask = pruner.compress()

Here is an example of L2NormPruner application.

Importing modules:

***Listing 6-7.*** L2NormPruner. ch6/algos/one\_shot/l2norm\_pruner.py

from nni.algorithms.compression.v2.pytorch.pruning import L2NormPruner

from ch6.algos.utils import oneshot\_prune, model\_comparison, visualize\_mask

from ch6.datasets import mnist\_dataset

from ch6.model.pt\_lenet import PtLeNetModel

Loading pre-trained model and MNIST dataset:

original = PtLeNetModel.load\_model()

train\_ds, test\_ds = mnist\_dataset()

Pruning convolutional layers of original model using L2NormPruner with 0.7

sparsity:

340

![](index-354_1.png)

Chapter 6 Model pruning

compressed, masks = oneshot\_prune(

original,

L2NormPruner,

\[{

'sparsity': .7,

'op\_types': \['Conv2d'\],

}\],

train\_ds

)

Visualizing prune mask:

visualize\_mask(masks)

Figur[e 6-6 vis](#index_split_003.html#p354)ualizes the mask of the compressed model. We see that the mask leaves 30% active weights for Conv2d layers.

***Figure 6-6.** L2NormPruner active weights*

And let’s compare the architectures of the original and compressed model:

model\_comparison(original, compressed, test\_ds, (1, 28, 28))

Original model has 0.991 accuracy, while the compressed one degrades to 0.98

accuracy. Ta[ble 6-5 com](#index_split_003.html#p355)pares the architectures of original and compressed models.

341

Chapter 6 Model pruning

***Table 6-5.** Original and L2Norm pruned model comparison*

**Layer**

**Original**

**Original**

**Pruned**

**Pruned**

**Output Shape**

**Size**

**Output Shape**

**Size**

Conv2d-1

\[16,24,24\]

416

**\[5,24,24\]**

**130**

Conv2d-2

\[32,20,20\]

12,832

**\[10,20,20\]**

**1,260**

Conv2d-3

\[32,6,6\]

25,632

**\[10,6,6\]**

**2,510**

Linear-4

\[64\]

18,496

\[64\]

5,824

Linear-5

\[32\]

2,080

\[32\]

2,080

Linear-6

\[10\]

330

\[10\]

330

**Total**

59,786

**12,134**

Table [6-5](#index_split_003.html#p355) shows that L2Norm Pruner compressed the original model almost five times, degrading from 0.991 to 0.98 accuracy.

**Iterative Pruners**

One-shot pruners are easy to use but have one major drawback. We must guess the

optimal sparsity values in advance. We usually want to maximize model compression without decreasing accuracy significantly. The natural solution would be to iterate several sparsity values to find the optimal one. This is exactly what iterative pruners were designed for. Pruning algorithms iteratively prune weights during optimization, which control the pruning schedule, including some automatic pruning algorithms.

After the iterative pruning algorithm completes all iterations, it selects the best pruned model according to specified score (it is not a necessary accuracy score). Figur[e 6-7](#index_split_003.html#p356)

demonstrates iterative pruning in action.

342

![](index-356_1.png)

Chapter 6 Model pruning

***Figure 6-7.** Iterative pruning*

This section will examine two popular iterative tuners: linear pruner and

AGP pruner.

**Linear Pruner**

Linear pruner is an iterative pruner. It will increase sparsity evenly from zero during each iteration. For example, the final sparsity is set as 0.5, and the iteration number is 5, and then the sparsity used in each iteration is \[0.1, 0.2, 0.3, 0.4, 0.5\].

343

![](index-357_1.png)

Chapter 6 Model pruning

LinearPruner is applied as follows:

from nni.algorithms.compression.v2.pytorch.pruning import LinearPruner

config\_list = \[{ 'sparsity': 0.8, 'op\_types': \['Conv2d'\] }\]

pruner = LinearPruner(

model = original,

config\_list = config\_list,

pruning\_algorithm = 'l1',

total\_iteration = 4,

finetuner = finetuner,

evaluator = finetuner,

speedup = True,

dummy\_input = dummy\_input\_tensor

)

pruner.compress()

\_, compressed, masks, best\_acc, best\_sparsity = pruner.get\_best\_result()

We will detail the Iterative Tuner configuration parameters in the “Iterative Pruner Configuration” section.

**AGP Pruner**

AGP is an iterative pruner, in which the sparsity is increased from an initial sparsity value *si* = 0 to a final sparsity value *sf* over a span of *n* pruning iterations, starting at training step *t0* and with pruning frequency Δ *t*:

For more details, please refer to the original paper “Exploring the efficacy of pruning for model compression” ([https://arxiv.org/pdf/1710.01878.pdf).](https://arxiv.org/pdf/1710.01878.pdf)

344

Chapter 6 Model pruning

AGPPruner is applied as follows:

from nni.algorithms.compression.v2.pytorch.pruning import AGPPruner

config\_list = \[{ 'sparsity': 0.8, 'op\_types': \['Conv2d'\] }\]

pruner = AGPPruner(

model = original,

config\_list = config\_list,

pruning\_algorithm = 'l1',

total\_iteration = 4,

finetuner = finetuner,

evaluator = finetuner,

speedup = True,

dummy\_input = dummy\_input\_tensor

)

pruner.compress()

\_, compressed, masks, best\_acc, best\_sparsity = pruner.get\_best\_result()

We will detail the Iterative Tuner configuration parameters in the “Iterative Pruner Configuration” section.

**Iterative Pruner Configuration**

Linear pruner and AGP pruner configuration is presented in Ta[ble 6-6.](#index_split_003.html#p359)

345

Chapter 6 Model pruning

***Table 6-6.** Iterative pruner configuration*

**Key**

**Description**

model

original pytorch model

config\_list

pruning configuration

pruning\_

(str) Specifies pruning algorithm.

algorithm

Supported choices: level, l1, l2, fpgm, slim, apoz,

mean\_activation, taylorfo, admm

total\_

(int) total number of iterations

iteration

log\_dir

(str) Specifies log directory to save results. You can find the best model pth

files in this folder

keep\_

(bool) if keeping the intermediate result, including intermediate model and

intermediate\_

masks during each iteration

result

finetuner

(Optional\[Callable\[\[Module\], None\]\]) Fine-tuner function that

retrains model after each pruning iteration

speedup

(bool) if set true, speed up the model at the end of each iteration to make

the pruned model compact

dummy\_input

(Optional\[torch.Tensor\]) if speedup is true, dummy\_input is required

for tracing the model in speed up

evaluator

(Optional\[Callable\[\[Module\], float\]\]) evaluate the pruned model

and give a score. if evaluator is none, the best result refers to the latest result pruning\_params (Dict) extra parameters for pruning\_algorithm implementation

**Iterative Pruning Scenarios**

This section will study two common use cases for iterative pruning.

346

![](index-360_1.png)

Chapter 6 Model pruning

**Best Accuracy Under Size Threshold Scenario**

A common problem is when we need to compress a model not to exceed a specified size threshold. In this case, it is necessary to choose the best model, which will be less than the specified size threshold. Figur[e 6-8 illus](#index_split_003.html#p360)trates how this can be done using iterative pruning.

***Figure 6-8.** Best accuracy under size threshold scenario*

Let’s handle this scenario to find the best compressed LeNet model that fits 30,000

model size (original size is 59,786) using iterative LinearPruner.

347

Chapter 6 Model pruning

Importing modules:

***Listing 6-8.*** Best accuracy under size threshold scenario. ch6/algos/iter/

linear\_pruner\_best\_acc\_scr.py

import os

import torch

from nni.algorithms.compression.v2.pytorch.pruning import LinearPruner

from ch6.algos.utils import model\_comparison

from ch6.datasets import mnist\_dataset

from ch6.model.pt\_lenet import PtLeNetModel

CUR\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_))

Loading original model:

original = PtLeNetModel.load\_model()

Specifying maximal sparsity for Conv2d and Linear layers:

config\_list = \[

{'sparsity': 0.85, 'op\_types': \['Conv2d'\]},

{'sparsity': 0.4, 'op\_types': \['Linear'\]},

{'op\_names': \['fc3'\], 'exclude': True} # excluding final layer

\]

Now we need to define a method that calculates the model’s score. All models whose size exceeds 30,000 will have a 0 score because we do not accept models larger than the specified size.

def evaluator(m: PtLeNetModel):

if m.count\_total\_weights() > 30\_000:

return 0

return m.test\_model()

Defining LinearPruner with 10 iterations and L1Norm pruning algorithm:

pruner = LinearPruner(

model = original,

config\_list = config\_list,

348

Chapter 6 Model pruning

pruning\_algorithm = 'l1',

total\_iteration = 10,

finetuner = lambda m: m.train\_model(epochs = 1),

evaluator = evaluator,

speedup = True,

dummy\_input = torch.rand(10, 1, 28, 28),

log\_dir = CUR\_DIR # logging results (model.pth and mask.pth is there)

)

Running iterative compression cycle:

pruner.compress()

Receiving results:

\_, compressed, masks, best\_score, best\_sparsity =\\

pruner.get\_best\_result()

The best pruned model is saved in ch6/algos/iter:

\# Best model saved in CUR\_DIR/<date/best\_result

print(f'Best Model is saved in: {CUR\_DIR}')

Now let’s analyze results returned by LinearPruner. First, let’s display a sparsity of each layer of the best pruned model:

print('===========')

print(f'Best accuracy: {best\_score}')

print('Best Sparsity:')

for layer in best\_sparsity:

print(f'{layer}')

Table [6-7](#index_split_003.html#p363) shows the sparsity of the best pruned model.

349

Chapter 6 Model pruning

***Table 6-7.** Sparsity of the best pruned model for*

*best accuracy under size threshold scenario*

**Layer**

**Sparsity**

conv1 (Conv2d)

0.19

conv2 (Conv2d)

0.003

conv3 (Conv2d)

0.16

fc1 (Linear)

0

fc2 (Linear)

0.085

And finally, let’s compare the original and the best pruned model:

\# Displaying comparison

train\_ds, test\_ds = mnist\_dataset()

model\_comparison(original, compressed, test\_ds, (1, 28, 28))

Original model has 0.991 accuracy, while the best compressed one that fits

30,000 size has 0.9913 accuracy. Table [6-8](#index_split_003.html#p363) compares the architectures of original and compressed models.

***Table 6-8.** Original and iteratively pruned by LinearPruner model comparison* **Layer**

**Original**

**Original**

**Pruned**

**Pruned**

**Output Shape**

**Size**

**Output Shape**

**Size**

Conv2d-1

\[16,24,24\]

416

**\[7,24,24\]**

**182**

Conv2d-2

\[32,20,20\]

12,832

**\[26,20,20\]**

**4,576**

Conv2d-3

\[32,6,6\]

25,632

**\[16,6,6\]**

**10,416**

Linear-4

\[64\]

18,496

**\[62\]**

**8,990**

Linear-5

\[32\]

2,080

**\[24\]**

**1,512**

Linear-6

\[10\]

330

\[10\]

**250**

**Total**

59,786

**25,926**

350

![](index-364_1.png)

Chapter 6 Model pruning

Great! We have significantly compressed the original LeNet model more than twice without losing accuracy.

**Minimal Size Above Accuracy Threshold Scenario**

Another case is to compress the model as much as possible while staying above the specified accuracy threshold. Figur[e 6-9 illus](#index_split_003.html#p364)trates how this can be done using iterative pruning.

***Figure 6-9.** Minimal size above specified accuracy threshold scenario*

Listin[g 6-9 h](#index_split_003.html#p365)andles this scenario to find the minimal compressed LeNet model that gives > 0.98 accuracy (original accuracy is 0.991) using iterative AGPPruner.

351

Chapter 6 Model pruning

Importing modules:

***Listing 6-9.*** Minimal size above specified accuracy threshold scenario. ch6/

algos/iter/agp\_pruner\_min\_size\_scr.py

import os

from math import inf

import torch

from nni.algorithms.compression.v2.pytorch.pruning import AGPPruner

from ch6.algos.utils import model\_comparison

from ch6.datasets import mnist\_dataset

from ch6.model.pt\_lenet import PtLeNetModel

CUR\_DIR = os.path.dirname(os.path.abspath(\_\_file\_\_))

Loading original model:

original = PtLeNetModel.load\_model()

Specifying maximal sparsity for Conv2d and Linear layers:

config\_list = \[

{'sparsity': 0.85, 'op\_types': \['Conv2d'\]},

{'sparsity': 0.4, 'op\_types': \['Linear'\]},

{'op\_names': \['fc3'\], 'exclude': True} # excluding final layer

\]

Now we need to define a method that calculates the model’s score. All models

whose accuracy is lower than 0.98 will have a -inf score because we do not accept such poor models. If the model performs better than 0.98, then its score is (-count\_total\_

weights):

def evaluator(m: PtLeNetModel):

acc = m.test\_model()

if acc < 0.98:

return -inf

return - m.count\_total\_weights()

352

Chapter 6 Model pruning

Defining AGPPruner with 20 iterations and L2Norm pruning algorithm:

pruner = AGPPruner(

model = original,

config\_list = config\_list,

pruning\_algorithm = 'l2',

total\_iteration = 20,

finetuner = lambda m: m.train\_model(epochs = 1),

evaluator = evaluator,

speedup = True,

dummy\_input = torch.rand(10, 1, 28, 28),

log\_dir = CUR\_DIR # logging results (model.pth and mask.pth is there)

)

Running iterative compression cycle:

pruner.compress()

Receiving results:

\_, compressed, masks, best\_score, best\_sparsity =\\

pruner.get\_best\_result()

The best pruned model is saved in ch6/algos/iter:

\# Best model saved in CUR\_DIR/<date/best\_result

print(f'Best Model is saved in: {CUR\_DIR}')

Now let’s analyze results returned by AGPPruner. First, let’s display a sparsity of each layer of the best pruned model:

print('===========')

print(f'Best accuracy: {best\_score}')

print('Best Sparsity:')

for layer in best\_sparsity:

print(f'{layer}')

Table [6-9](#index_split_003.html#p367) shows the sparsity of the best pruned model.

353

Chapter 6 Model pruning

***Table 6-9.** Sparsity of the best pruned model for*

*minimal size above accuracy threshold scenario*

**Layer**

**Sparsity**

conv1 (Conv2d)

0.13

conv2 (Conv2d)

0

conv3 (Conv2d)

0.13

fc1 (Linear)

0

fc2 (Linear)

0.03

And finally, let’s compare the original and the best pruned model:

\# Displaying comparison

train\_ds, test\_ds = mnist\_dataset()

model\_comparison(original, compressed, test\_ds, (1, 28, 28))

Original model has 0.991 accuracy and 59,786 size, while the minimal model that

exceeds 0.98 accuracy has 0.9883 accuracy and 11,535 size. Table [6-10 com](#index_split_003.html#p367)pares the architectures of original and compressed models.

***Table 6-10.** Original and iteratively pruned by AGPPruner model comparison* **Layer**

**Original**

**Original**

**Pruned**

**Pruned**

**Output Shape**

**Size**

**Output Shape**

**Size**

Conv2d-1

\[16,24,24\]

416

**\[3,24,24\]**

**78**

Conv2d-2

\[32,20,20\]

12,832

**\[24,20,20\]**

**1,824**

Conv2d-3

\[32,6,6\]

25,632

**\[7,6,6\]**

**4,207**

Linear-4

\[64\]

18,496

**\[61\]**

**3,904**

Linear-5

\[32\]

2,080

**\[21\]**

**1,302**

Linear-6

\[10\]

330

\[10\]

**220**

**Total**

59,786

**11,535**

354

Chapter 6 Model pruning

Yes, the accuracy of the original model degraded from 0.991 to 0.9883, but we

compressed the original model more than five times! We made our model lightweight, and now it is more attractive for economical usage.

In this section, we have demonstrated the practical use of iterative pruners in real-world cases. We see that iterative pruning significantly benefits practical deep learning deployment problems.

NNI provides a rich set of pruning algorithms:

• Slim Pruner

• Activation APoZ Rank Pruner

• Activation Mean Rank Pruner

• Taylor FO Weight Pruner

• ADMM Pruner

• Movement Pruner

• Lottery Ticket Pruner

• Simulated Annealing Pruner

• Auto Compress Pruner

• AMC Pruner

Please refer to the official documentation for more details[: https://nni.](https://nni.readthedocs.io)

[readthedocs.io.](https://nni.readthedocs.io)

**Summary**

Pruning is an essential part of automated deep learning. It denotes the neural network complexity problem. In addition to the fact that we need an accurate neural network, we also need a lightweight neural network. We will always prefer a neural network with 1M parameters over a neural network with 10M parameters if they have the same accuracy. In this chapter, we have covered the basic principles of model pruning using NNI. Model pruning is a significant direction of neural network optimization that allows the integration of machine learning models into simple devices.

355

**CHAPTER 7**

**NNI Recipes**

In the previous chapters, we studied various NNI features and applications. NNI is a very efficient automated deep learning tool that solves complex deep learning problems.

We have witnessed that many NNI experiments can last days or even weeks. Therefore, it is crucial to organize experiments properly. Otherwise, a lot of valuable information and efforts can be lost. On the other hand, NNI uses sophisticated mathematical search algorithms to find the optimal solution in the shortest time in the vast search space.

Time is a precious resource. So it is also essential to speed up the NNI execution, which will help maximize the efficiency. It is great to understand the mathematical core of algorithms NNI implements, but it is also important to know how to use NNI effectively.

This chapter will examine patterns and recipes that can help make NNI interactions much more effective. These recipes should help speed up, stabilize, and make research and experiments more developer friendly.

**Speed Up Trials**

It is essential to speed up the Trial execution in HPO and Multi-trial NAS. The

completion of the search algorithm depends on the duration of the Trials, so Trial speed optimization is the first thing a developer should start with. Here, we will mention basic rules a reader should follow to construct a fast Trial.

**Use the GPU**. One of the most common ways to speed up neural network

computations is to use a GPU. Properly configuring the model for GPU usage is the developer’s responsibility. If your machine has GPUs, ensure they are utilized during NNI Trial execution.

**Do not download dataset twice**. A common mistake is downloading heavy datasets without caching them on the disk. Please make sure that the downloaded dataset is cached on disk and the trial does not attempt to download ten gigabytes from the Internet each time it runs a new trial.

357

© Ivan Gridin 2022

I. Gridin, *Automated Deep Learning Using Neural Network Intelligence*,

[https://doi.org/10.1007/978-1-4842-8149-9\_7](https://doi.org/10.1007/978-1-4842-8149-9_7#DOI)

![](index-370_1.png)

Chapter 7 NNI reCIpes

**Use the duration panel** to determine the longest-running Trials. This can help in finding abnormally long Trials. Figur[e 7-1 sho](#index_split_003.html#p370)ws NNI duration panel.

***Figure 7-1.** Duration panel*

**Use dry trial runs** to debug trials. Each trial can be run manually as a Python script, which can help find performance issues and bottlenecks. Try running the Trial several times to check its performance before launching the experiment.

**Start–Stop–Resume**

Keep in mind that each experiment can be manually stopped and resumed after. All experiment information is stored in the NNI output folder (path is defined by NNI\_

OUTPUT\_DIR environment variable, ~/nni-experiments by default). Therefore, you can stop the experiment at any time using the following command:

nnictl stop <experiment\_id>

and resume it with

nnictl resume <experiment\_id>

You can resume an embedded experiment using the following script:

from time import sleep

from nni.experiment import Experiment

experiment = Experiment('local')

358

![](index-371_1.png)

Chapter 7 NNI reCIpes

experiment.resume('experiment\_id', port)

while True:

sleep(1)

if experiment.get\_status() == 'DONE':

break

This could be useful when you need to restart an execution machine or an

experiment crashed for some reason. It is also possible to resume a finished experiment to re-analyze its results.

**Continue Finished Experiment**

Suppose the experiment stopped meeting terminal condition (maxTrialNumber or

maxExperimentDuration), but you are not satisfied with the results and want to continue the experiment. In that case, you can resume the finished experiment by changing the terminal condition in WebUI. For example, Figur[e 7-2](#index_split_003.html#p371) illustrates maxTrialNumber update.

***Figure 7-2.** Updating maxTrialNumber*

You can also use the WebUI to update the Experiment configuration and

search space.

**NNI and TensorBoard**

NNI can be integrated with TensorBoard. This is very practical if you want to visualize additional Trial metrics. Let’s look at an example of integrating NNI with TensorBoard.

Make sure tensorboard is installed in your environment. Listin[g 7-1 illus](#index_split_003.html#p372)trates a dummy Trial implementation that writes metrics using TensorBoard format.

359

Chapter 7 NNI reCIpes

***Listing 7-1.*** NNI and TensorBoard. ch7/tb/trial.py

import os

from random import random

import nni

The simplest way is to use torch.utils.tensorboard.SummaryWriter class to export metrics to tensorboard logs:

from torch.utils.tensorboard import SummaryWriter

Initializing SummaryWriter:

log\_dir = os.path.join(os.environ\["NNI\_OUTPUT\_DIR"\], 'tensorboard')

writer = SummaryWriter(log\_dir)

Trial entry point:

if \_\_name\_\_ == '\_\_main\_\_':

p = nni.get\_next\_parameter()

for i in range(100):

Calculating dummy metrics:

acc = min((i + random() \* 10) / 100, 1)

loss = max((100 - i + random() \* 10) / 100, 0)

Writing metrics to tensorboard log:

writer.add\_scalar('Accuracy', acc, i)

writer.add\_scalar('Loss', loss, i)

nni.report\_intermediate\_result(acc)

nni.report\_final\_result(acc)

You can run dummy experiment that uses Trial from Listin[g 7-1 us](#index_split_003.html#p372)ing the following command:

nnictl create --config=ch7/tb/config.yml

360

![](index-373_1.png)

Chapter 7 NNI reCIpes

Once the experiment has started, you can go to the Trial jobs panel on Trails detail page, select Trials you want to analyze, and click TensorBoard button, as shown in Figur[e 7-3.](#index_split_003.html#p373)

***Figure 7-3.** Launching TensorBoard*

After clicking the TensorBoard button, NNI starts the TensorBoard process passing Trial log directories as its input and redirects the browser to its web page. Figur[e 7-4](#index_split_003.html#p374)

shows TensorBoard panel with metrics we have collected during dummy trials we

defined in Listing [7-1](#index_split_003.html#p372).

361

![](index-374_1.png)

Chapter 7 NNI reCIpes

***Figure 7-4.** TensorBoard displaying Trial metrics*

NNI runs an actual TensorBoard process, so you can stop it when you’re done with it, as shown in Figur[e 7-5.](#index_split_003.html#p375)

362

![](index-375_1.png)

![](index-375_2.png)

Chapter 7 NNI reCIpes

***Figure 7-5.** Stopping TensorBoard process*

Integrating TensorBoard in your NNI Experiments can help you analyze Trial results and whole Experiment progress.

**Move Experiment to Another Server**

All information about the Experiment is stored in the NNI\_OUTPUT\_DIR/<experiment\_id> folder (~/nni-experiments/<experiment\_id> by default), so you can easily move the experiment data to another server to resume it there. You just need to stop the Experiment, move the folder to another server, and resume the Experiment. Figur[e 7-6](#index_split_003.html#p375)

illustrates this approach.

***Figure 7-6.** Moving Experiment to another server*

You can use this trick if you want to move your experiment to a more powerful server or if you want to share the results of an experiment.

363

![](index-376_1.png)

Chapter 7 NNI reCIpes

**Scaling Experiments**

Scaling is the most natural approach to speed up Experiment execution. You can use multiple servers to distribute Trial jobs. NNI implements the Training Service concept.

Training Service is an environment that performs Trial jobs. We have only used the Local Training Service in this book, which means that all calculations are done on the local machine. But you can organize an Experiment using various Remote Training Services.

NNI 2.7 supports the following environments as Training Services:

• **Local**: Running Trial jobs on local machine

• **Remote**: Running Trial jobs on remote machine using ssh

• **OpenPAI**: Running Trial jobs on Microsoft Open Platform for

AI server

• **AML**: Running Trial jobs on Azure Machine Learning server

• **Hybrid**: Allows setting several different Training Services

Many search algorithms allow concurrent Trial execution, so you can horizontally scale the experiment, significantly increasing its speed. Figur[e 7-7 illus](#index_split_003.html#p376)trates this concept.

***Figure 7-7.** Horizontal scaling*

Let’s look at an example configuration that uses the Remote Training Service.

Common configuration part:

trialConcurrency: 4

maxTrialNumber: 100

searchSpace:

364

Chapter 7 NNI reCIpes

x:

\_type: quniform

\_value: \[1, 100, 0.1\]

trialCodeDirectory: .

trialCommand: python3 trial.py

tuner:

name: Random

Remote Training Service settings. nniManagerIp is used as the host Experiment

address to send metrics from Trial jobs running on remote machines:

nniManagerIp: <nni\_host\_ip> # example: 10.10.120.20

trainingService:

platform: remote

Listing remote machines with ssh access:

machineList:

\- host: <remote1\_ip> # example: 10.10.120.21

user: <remote1\_ssh\_user> # example: nni\_user

password: <remote1\_ssh\_pass> # example: nni\_user\_pass

pythonPath: <remote1\_ssh\_pass> # example: /opt/python3/bin

\- host: <remote2\_ip> # example: 10.10.120.22

user: <remote2\_ssh\_user> # example: nni\_user

password: <remote2\_ssh\_pass> # example: nni\_user\_pass

pythonPath: <remote2\_ssh\_pass> # example: /opt/python3/bin

You can apply Remote Training Service in embedded (stand-alone) NNI mode as

follows:

\# Loading Packages

from nni.experiment import Experiment, RemoteConfig, RemoteMachineConfig

from pathlib import Path

Remote Training Service parameters:

365

Chapter 7 NNI reCIpes

nni\_host\_ip = '10.10.120.20'

remote\_ip = '10.10.120.21'

remote\_ssh\_user = 'nni\_user'

remote\_ssh\_pass = 'nni\_pass'

remote\_python\_path = '/opt/python3/bin'

Common Experiment configuration:

\# Defining Search Space

search\_space = {

"x": {"\_type": "quniform", "\_value": \[1, 100, .1\]}

}

\# Experiment Configuration

experiment = Experiment('remote')

experiment.config.experiment\_name = 'Remote Experiment'

experiment.config.trial\_concurrency = 4

experiment.config.trial\_command = 'python3 trial.py'

experiment.config.trial\_code\_directory = Path(\_\_file\_\_).parent

experiment.config.max\_trial\_number = 1000

experiment.config.search\_space = search\_space

experiment.config.tuner.name = 'Random'

Remote Training Service configuration:

experiment.config.nni\_manager\_ip = nni\_host\_ip

remote\_service = RemoteConfig()

remote\_machine = RemoteMachineConfig()

remote\_machine.host = remote\_ip

remote\_machine.user = remote\_ssh\_user

remote\_machine.password = remote\_ssh\_pass

remote\_machine.python\_path = remote\_python\_path

remote\_service.machine\_list = \[remote\_machine\]

experiment.config.training\_service = remote\_service

Starting NNI:

http\_port = 8080

experiment.start(http\_port)

366

![](index-379_1.png)

Chapter 7 NNI reCIpes

Processing event loop:

while True:

if experiment.get\_status() == 'DONE':

break

The remote server must have the same Python environment installed as the

Experiment host server. NNI copies the experiment information to the remote server and executes the Trial jobs during the experiment. Here is an example of a Trial process executed on a remote server:

python3 -m nni.tools.trial\_tool.trial\_runner --job\_pid\_file /tmp/nni-

experiments/5jixfy3o/envs/XfJ9j/pid

NNI provides rich explanations concerning Training Services. Please refer to the official documentation for more details: [https://nni.readthedocs.io/.](https://nni.readthedocs.io/)

**Shared Storage**

NNI scaling we considered in the previous section has one serious drawback. Training Services return only Trial metrics (nni.report\_intermediate\_result and nni.report\_

final\_result) to Experiment host server. All Trial logs are stored on the machine they are executed as shown in Figure [7-8](#index_split_003.html#p379).

***Figure 7-8.** Local logging*

367

![](index-380_1.png)

Chapter 7 NNI reCIpes

This is not convenient because the logs are located in different places.

To solve this problem, NNI provides a Shared Storage implementation that allows

you to store all Trial logs in one place, accessible to the NNI Experiment. Figur[e 7-9](#index_split_003.html#p380)

depicts architecture of NNI Experiment with Shared Storage.

***Figure 7-9.** Shared Storage*

There are two ways to implement Shared Storage in Experiment: NFS and Azure

Blob. Here is a sample configuration for NFS Shared Storage:

\# Experiment Configuration

...

\# Training Service Configuration

...

\# Shared Storage Configuration

sharedStorage:

storageType: NFS

localMountPoint: ${your/local/mount/point}

remoteMountPoint: ${your/remote/mount/point}

nfsServer: ${nfs-server-ip}

exportedDirectory: ${nfs/exported/directory}

localMounted: nnimount

\# Values for localMounted:

368

Chapter 7 NNI reCIpes

\# usermount: means you have already mount this storage on

localMountPoint

\# nnimount: means nni will try to mount this storage on localMountPoint

\# nomount: means storage will not mount in local machine, will support

partial storages in the future

Please refer to the official documentation for more details concerning Shared Storage implementation: [https://nni.readthedocs.io/](https://nni.readthedocs.io/).

**One-Shot NAS with Checkpoints and TensorBoard**

All of the patterns we have studied in this chapter are suitable for HPO and Multi-trial NAS, but they are useless for One-shot NAS. Indeed, One-shot NAS is an exceptional case, and it has the following limitations:

• Cannot be stopped and resumed

• Does not have a visualization of the training process

• Cannot be restored after an error occurs

• Cannot be transferred to another server

These are pretty serious limitations, making working with such an effective method much more difficult. Let’s try to eliminate all these limitations on the example of PyTorch LeNet Supernet (ch7/one\_shot\_nas/pt\_lenet.py) and DartsTrainer implementation.

DartsTrainer accepts a user-defined method that calculates Supernet accuracy

during the training process. To visualize the training process, we can use tensorboard logging with SummaryWriter that logs each training iteration’s accuracy. Listing [7-2](#index_split_003.html#p381)

demonstrates how to visualize training progress.

(Full code is provided in the corresponding file: ch7/one\_shot\_nas/pt\_utils.py.)

***Listing 7-2.*** Injecting TensorBoard logging in accuracy method

from torch.utils.tensorboard import SummaryWriter

Initializing SummaryWriter:

cd = os.path.dirname(os.path.abspath(\_\_file\_\_))

dt = datetime.now().strftime("%Y-%m-%d\_%H-%M-%S")

369

Chapter 7 NNI reCIpes

tb\_summary = SummaryWriter(f'{cd}/runs/{dt}')

iter\_counter = 0

Method that calculates Supernet accuracy for DartsTrainer:

def accuracy(output, target, topk = (1,)):

global iter\_counter

...

Calculating results:

res = dict()

for k in topk:

correct\_k = correct\[:k\].reshape(-1).float().sum(0)

accuracy = correct\_k.mul\_(1.0 / batch\_size).item()

Passing accuracy to TensorBoard logs:

tb\_summary.add\_scalar('darts\_lenet', accuracy, iter\_counter)

iter\_counter += 1

res\["acc{}".format(k)\] = accuracy

return res

Injecting TensorBoard logging in accuracy method allows visualizing Supernet

training progress. But the main problem is that the One-shot NAS process is very fragile.

If the server crashes or an OutOfMemory error occurs, the One-shot NAS process will be stopped without the possibility of resuming. This is a very serious risk of losing valuable results and time. Let’s try to solve this problem. We need to mention that One-shot NAS

training uses a training loop like most neural networks. The One-shot NAS algorithm takes specific actions to converge to the optimal subnet during each training epoch.

When we run the trainer fit method, we run the training loop. But this training loop can be run several times, and each time a new training loop will train the Supernet model from DartsTrainer. So we can split one fit method with num\_epochs = 50 into five fit methods with num\_epochs = 10. Figure [7-10](#index_split_003.html#p383) illustrates this concept.

370

![](index-383_1.png)

Chapter 7 NNI reCIpes

***Figure 7-10.** Shared Storage*

And what we can do is dump a binary image of DartsTrainer between training

subcycles creating checkpoints, as shown in Figure [7-11.](#index_split_003.html#p384)

371

![](index-384_1.png)

Chapter 7 NNI reCIpes

***Figure 7-11.** One-shot NAS with checkpoints*

This trick allows us to solve all main problems concerning the One-shot NAS

process:

• Process can be resumed if machine crashes.

• Process can be stopped manually and resumed after.

• Checkpoint can be moved to another machine and resumed there.

Listin[g 7-3 demons](#index_split_003.html#p385)trates how One-shot NAS process with checkpoint dumping can be implemented.

We are using pickle to dump trainer binary image (please install this package if necessary):

372

Chapter 7 NNI reCIpes

***Listing 7-3.*** One-shot NAS with checkpoints. ch7/one\_shot\_nas/darts\_train\_

with\_checkpoint.py

import pickle

Importing other modules:

import os

from os.path import exists

import torch

import torch.nn as nn

import ch7.datasets as datasets

from nni.retiarii.oneshot.pytorch import DartsTrainer

from ch7.one\_shot\_nas.pt\_lenet import PtLeNetSupernet

from ch7.one\_shot\_nas.pt\_utils import accuracy

Specifying trainer checkpoint path:

cd = os.path.dirname(os.path.abspath(\_\_file\_\_))

trainer\_checkpoint\_path = f'{cd}/darts\_trainer\_checkpoint.bin'

Following method created DartsTrainer for LeNet Supernet:

def get\_darts\_trainer():

\# Supernet

model = PtLeNetSupernet()

\# Dataset

dataset\_train, dataset\_valid = datasets.get\_dataset("mnist")

\# Loss Function

criterion = nn.CrossEntropyLoss()

\# Optimizer

optim = torch.optim.SGD(

model.parameters(), 0.025,

momentum = 0.9, weight\_decay = 3.0E-4

)

\# Trainer params

num\_epochs = 0

373

Chapter 7 NNI reCIpes

batch\_size = 256

metrics = accuracy

\# DARTS Trainer

darts\_trainer = DartsTrainer(

model = model,

loss = criterion,

metrics = metrics,

optimizer = optim,

num\_epochs = num\_epochs,

dataset = dataset\_train,

batch\_size = batch\_size,

log\_frequency = 10,

unrolled = False

)

return darts\_trainer

The following method trains Supernet for specified number of epochs and dumps

trainer:

def train\_and\_dump(darts\_trainer, epochs):

"""

Trains Supernet according to DARTS algorithm

"""

darts\_trainer.num\_epochs = epochs

darts\_trainer.fit()

with open(trainer\_checkpoint\_path, 'wb') as f:

pickle.dump(darts\_trainer, f)

return darts\_trainer

And here is the main script that loads the trainer from binary checkpoint if necessary and splits the whole training loop into multiple subcycles:

if \_\_name\_\_ == '\_\_main\_\_':

if exists(trainer\_checkpoint\_path):

374

Chapter 7 NNI reCIpes

with open(trainer\_checkpoint\_path, 'rb') as f:

trainer = pickle.load(f)

else:

trainer = get\_darts\_trainer()

for \_ in range(10):

trainer = train\_and\_dump(trainer, epochs = 5)

print(f'Best model: {trainer.export()}')

Now let’s run the script (ch7/one\_shot\_nas/darts\_train\_with\_checkpoint.py) we

examined in Listing [7-3](#index_split_003.html#p385). We can visualize One-shot NAS process with TensorBoard: tensorboard --logdir=ch7/one\_shot\_nas/runs/

And now, we can monitor Supernet training progress using the following link:

http://localhost:6006/#scalars. Figur[e 7-12 demons](#index_split_003.html#p388)trates TensorBoard web page.

375

![](index-388_1.png)

Chapter 7 NNI reCIpes

***Figure 7-12.** Supernet training progress*

But the most important thing is that you can stop the execution of ch7/one\_shot\_

nas/darts\_train\_with\_checkpoint.py script and then run it again. DartsTrainer will be restored from the binary checkpoint file ch7/one\_shot\_nas/darts\_trainer\_checkpoint.

bin and continue Supernet training. Figur[e 7-13](#index_split_003.html#p389) shows that DartsTrainer continues training from the checkpoint, not from scratch.

376

![](index-389_1.png)

Chapter 7 NNI reCIpes

***Figure 7-13.** One-shot NAS training resume*

This technique allows the implementation of really long-term One-shot NAS

Experiments without fear that the Experiment or the server will crash. You can also stop and resume Experiment at any convenient time.

**Summary**

This chapter examined several tricks and patterns that can facilitate your user

experience. NNI is an open source developer-friendly framework, so you can implement your own ideas and approaches in your research and experiments. In this chapter, we complete the book. I hope that you now can appreciate the effectiveness of using the NNI framework, and it can become an indispensable tool for your daily research activity.

377

**Index**

**A**

Black-box function, 13–18, 22, 27, 28, 112,

113, 116, 124, 128, 130, 132, 142,

Abstract LeNet model design, 54

184, 196

Ackley’s function, 148, 149

Block operation, 300, 301

Activation design

Bottleneck block space, 236

hyperparameter, 72

Box prediction algorithm, 3

Adam optimizer, 56, 58, 97, 103

AGP pruner, 343–345

Annealing algorithm flow, 123

**C**

Anneal Tuner

Choice sampling strategy, 41

annealing algorithm, 122, 123

CIFAR-10, 221, 222

configuration, 124

CIFAR-10 ResNet NAS, 236–246

generation, 126, 128

Classic Neural Architecture Search

optimizing holder\_function, 125

(TensorFlow)

holder’s black-box function, 124

base model, 247, 248

AutoDL approaches, 318

experiment, 252, 254, 255

Automated deep learning (AutoDL)

mutators, 248–250

adapting model to

search space, 251

new dataset, 8

search strategy, 252

definition, 2

trial, 250

injecting technique, 7

Conv2D layers, 55, 335, 341

neural architecture search, 8

Cross-entropy loss function, 58, 64, 103

No Free Lunch theorem, 3–6

Curve fitting assessor, 162, 163

sections, 2

Curve Fitting prediction, 163

solving practical problems, 9

Customized trial, 24

source code, 9

Custom Tuner, internals, 144–147,

Automated machine learning

*See also* New Evolution Custom Tuner

(AutoML), 1, 2, 9

**D**

**B**

DartsTrainer, 297, 369

Base model, 197–201, 236, 247, 248, 250

Data flow graph (DFG), 186

Benchmark algorithm, 143

Decision maker hyperparameters, 91, 94

379

© Ivan Gridin 2022

I. Gridin, *Automated Deep Learning Using Neural Network Intelligence*,

[https://doi.org/10.1007/978-1-4842-8149-9](https://doi.org/10.1007/978-1-4842-8149-9#DOI)

INDEX

Deep learning, 1, 2, 107, 109, 110, 144, 157,

optimizing black\_box\_f1 function, 118

158, 164, 166, 182, 183, 185

configuration, 118

Deep neural networks (DNNs), 187

experiment, 118

Design hyperparameter, 34, 39, 40,

search principle, 117

72, 73, 255

search space by generations, 119–121

Differentiable Architecture

selection and mutation, 117

Search (DARTS)

Experiment file structure, 52

in action, 297

Exploration strategies

algorithm, 300

grid search, 215

DartsTrainer parameters, 298

random strategy, 215

operation relaxation, 296

regularized evolution, 215–218

PyTorch, 298

RL, 218–220

Dropout design hyperparameter, 72, 73

TPE, 218

Dropout technique, 71, 110

**F**

**E**

FactorizedReduced layer, 301, 309

Efficient Neural Architecture

FCNN model weights and biases, 33

Search (ENAS)

Feature engineering, 2

automatic model design, 282

Feature extraction and decision maker

EnasTrainer parameters, 290

components, 87

GeneralSupernet best architecture, 309

Feature Extraction block, 222–224, 227, 230

initial epoch, 287

Feature extraction hyperparameters,

middle training, 288

89, 98, 105

NNI, 289

Feature hyperparameter, 34, 36–38

practice, 286

Filter pruning via geometric median

PyTorch implementation, 293–295

(FPGM) pruner, 337, 339

RL Controller subnet selection, 283

Fully Connected block, 227

TensorFlow implementation, 291–293

Fully Connected block space, 223

training loop, 284

weight sharing, 284

Efficient neural architecture search via

**G**

parameter sharing (ENAS),

Gaussian Process (GP) Tuner

257, 282

concurrency issue, 141

EnasTrainer parameters, 289, 290

configuration, 138

Evaluator, 185, 197, 214, 215, 220

holder\_function optimization, 141

EvolutionShrinkTuner, 177, 178

Holder’s black-box function

Evolution Tuner

optimization, 142

380

INDEX

parameters, 139, 140

**L**

search space types, 140

L1Norm Pruner, 340–342

GeneralSupernet

L2Norm Pruner, 340–342

architecture, 301

LayerChoice mutator, 190, 200, 248

block operation, 301

Layer hyperparameter, 35, 55, 68

cell, 301

Layer hyperparameter optimization, 55

definition, 300

learning\_rate hyperparameter, 94, 103

LayerChoice, 300

Learning rate tuning, 35

PyTorch and DARTS, 310–317

Learning rate problem, 35, 36

TensorFlow and ENAS, 303–309

LeNet architecture, 54, 71, 72

Grid search strategy, 215

LeNet evolution model

Grid search tuner, 48, 108, 116

decision maker

hyperparameters, 91, 94

**H**

design hyperparameters, 89

Holder’s function, 124, 125

feature extraction hyperparameters, 89

Horizontal scaling, 364

HPO experiment, 107–110

Hyperparameter, 34

HPO search space, 92

Hyperparameter optimization

hyperparameters, 95, 109

(HPO), 2, 31

PyTorch Lightning, 100–107

Hyperparameter panel, 21, 23,

TensorFlow implementation, 94–100

63, 68, 84

LeNet failed predictions, 68, 71

Hyperparameters

LeNet HPO experiment, 66–71

Hyperparameter

LeNet HPO search space, 56

Optimization, 183

LeNet model

LeNet Evolution, 109

feature extraction and decision

LeNet Evolution model, 89

making, 86

LeNet model, 55, 57

filter\_size, 56

handwritten digit recognition

**I, J, K**

problem, 55

kernel\_size, 56

InputChoice mutator, 202–209

layer hyperparameters, 55

Iterative pruner configuration, 346

out\_features, 56

Iterative pruners, 342, 343

PyTorch implementation, 61–66

Iterative pruning scenarios

with ReLU and Dropout, 71–74

best accuracy under size

TensorFlow implementation, 57–60

threshold, 347–351

LeNet Model Pruning, 322–328

minimal size above accuracy

LeNet NAS Best Model Architecture, 235

threshold, 351–355

LeNet NAS Model Space, 224

381

INDEX

LeNet One-shot Model Space, 277

**N**

LeNet Upgrade model

Natural language processing (NLP)

HPO experiment, 82–85

problems, 36

PyTorch implementation, 78–82

Netron model visualization, 195

TensorFlow Implementation, 75–78

Neural architecture search (NAS), 2, 8,

Level pruner, 334, 336, 337

40, 182–187

Linear layer, 55

data flow graph, 186

Linear pruner, 343

Retiarii (PyTorch)

Local logging, 367

Base Model, 198

Lognormal sampling, 43

chain of operators F, 188

Loguniform sampling, 43

CIFAR-10 LeNet NAS, 221–224

CIFAR-10 ResNet NAS, 236–246

**M**

data flow graph model space, 189

evaluators, 214

Machine learning models, 1, 2, 194, 355

experiment, 191, 220, 221

Machine learning operators, 168, 169

exploration strategies ( *see*

MaxPool2D layer, 55, 56

Exploration strategies)

maxTrialNumber,17, 26, 66

framework, 196

Median stop, 158–162

launching, 192, 193

Metric panel, 21, 140, 155

Model Space, 190

MlPipelineClassifier, 175

Mutators ( *see* Mutators)

MNIST Classifier problem, 52

visualization panel, 194

MNIST database, 53

Neural network intelligence (NNI)

Model compression, 2

API, 50

Model Pruning

black-box function optimization, 13–18

application, 321

command line, 24

configuration, 333, 334

Docker, 11, 12

description, 319, 320

embedded, 27, 28

LeNet, 322–328

experiment configuration, 25, 26

Model Space, 190, 196, 197

installation, 10, 11

Multi-connected neural network, 183

search space, tuner, and trial, 12, 13

Multi-trial NAS, 185, 317

New Evolution Custom Tuner

Mutators, 197, 248–250

Ackley’s function, 148, 149

InputChoice, 201–208

binary classification problem, 166–168

labeling, 212

curve fitting, 162, 163

LayerChoice, 200

early stopping, 156–158

repeat, 209–212

experiment, 179, 180, 182

ValueChoice, 201

experiment configuration, 153

382

INDEX

generate\_parameters method, 153

One-shot pruning

good trial early stopped, 164

algorithms, 329–332

“hill-climbing” approach, 148

Operators, 168, 169, 171

Individual and Population classes, 152

Organizing experiment, 48–52

locations visited by population, 155

median stop, 158–162

model, 175, 177

**P**

operators, 168, 171

Pruner configuration, 333, 334

optimal functional pipeline and

Pruning algorithm, 320, 329, 332, 342

classical AutoML, 164

PyTorch, 29, 30

population class, 150

PyTorch ENAS implementation, 293–295

Python embedded experiment, 154

PyTorchL, LeNet Upgrade model

replace\_worst, 151

implementation, 78–82

search approach, 147

PyTorch LeNet implementation, 61–66

search space, 171, 172, 174, 177

PyTorch Lightning, 100–107

super().generate\_parameters, 178

trial metric panel, 155

update\_search\_space method, 152

**Q**

nni.get\_next\_parameter() method, 50, 51

quniform sampling strategy, 44

NNI, TensorBoard, 359, 361, 363

No Free Lunch (NFL) theorem, 3–6

**R**

Random search tuner, 47, 114, 115

**O**

Random strategy, 215

One-Shot algorithms, 257, 281, 282, 300,

Regularized evolution strategy, 215–218

317, 318

Repeat mutator, 209–212, 226, 229, 231

One-shot Neural Architecture Search, 317

Residual Cell space, 237

with Checkpoints and

ResNet architecture, 209

TensorBoard, 369–377

ResNet NAS Model Space, 241

mask parameter, 266, 268

ResNet NAS space, 238

model space for MNIST problem, 258

Retiarii evaluator, 214

multi-trial NAS results, 265

RL strategy, 215, 218–220, 289

PyTorch implementation, 262, 263,

267, 270

results, 271

**S**

supernet, 259, 260, 272

Scaling experiments, 364, 366, 367

TensorFlow implementation, 263, 269

Search algorithm, 143, 215, 357

training resume, 377

Search space, 15

383

INDEX

Search space ( *Cont*.)

ENAS implementation, 291–293

choice, 41

LeNet evolution model

deep learning model, 45

implementation, 94–100

lognormal, 43

LeNet Upgrade model

loguniform, 42

implementation, 75–78

normal, 43

TensorFlow LeNet implementation, 57–60

qlognormal, 43

TPE strategy, 218

qloguniform, 43

Training hyperparameter, 35, 36, 69

qnormal, 43

Tree-structured Parzen Estimator

quniform, 42

Tuner (TPE)

randomint, 42

configuration, 134

uniform, 42

“Good” and “bad” separation, 133

Search tuners, 46–48, 67, 83, 108, 111–114

optimizing holder\_function, 136

Sequential model-based optimization

next candidate selection, 134

(SMBO) Tuners, 128–132

parameters, 134, 135

Shallow learning, 2

search progress, 136, 138

Shared storage, 367, 368

Trial hyperparameters, 67, 83

Shared Storage, 371

Trial list panel, 23

Simulated Annealing algorithm, 122

trial method, 60, 65, 81

Speed up trials, 357, 358

Trial numbers panel, 19

Start–stop–resume, 358

Trials details page, 20, 22–24

Supernet architecture, 258, 260

Tuners, 12, 46, 111

convolution layer, 278–281

forward method, 281

**U, V**

helper function, 280

use\_dropout design hyperparameter, 72

LayerChoice and InputChoice

use\_dropout hyperparameter, 74

methods, 277

model space, 273

One-shot NAS, 274

**W, X, Y, Z**

size tensor outputs, 276

Web user interface

subnet evaluation, 275

embedded NNI, 27, 28

Supernet training progress, 370, 376

NNI command line, 24

NNI experiment configuration, 25, 26

overview page, 18, 20

**T**

TensorFlow and PyTorch, 29

Task parameters, 32

trials details page, 20, 22–24

TensorFlow

troubleshooting, 28, 29

384

# Document Outline

*   [Table of Contents](#index_split_000.html#p4)
*   [About the Author](#index_split_000.html#p9)
*   [About the Technical Reviewer](#index_split_000.html#p10)
*   [Introduction](#index_split_000.html#p11) 
    *   [Source Code Listings](#index_split_000.html#p13)
*   [Chapter 1: Introduction to Neural Network Intelligence](#index_split_000.html#p14) 
    *   [What Is Automated Deep Learning?](#index_split_000.html#p14) 
        *   [No Free Lunch Theorem](#index_split_000.html#p16)
        *   [Injecting New Deep Learning Techniques into Existing Model](#index_split_000.html#p19)
        *   [Adjusting Model to a New Dataset](#index_split_000.html#p20)
        *   [Creating a New Model from Scratch](#index_split_000.html#p21)
        *   [Reinventing the Wheel](#index_split_000.html#p22)
    *   [Working with Source Code](#index_split_000.html#p22)
    *   [Neural Network Intelligence Installation](#index_split_000.html#p22) 
        *   [Install](#index_split_000.html#p23)
        *   [Docker](#index_split_000.html#p24)
        *   [Search Space, Tuner, and Trial](#index_split_000.html#p25)
        *   [Black-Box Function Optimization](#index_split_000.html#p26)
    *   [Web User Interface](#index_split_000.html#p31) 
        *   [Overview Page](#index_split_000.html#p31)
        *   [Trials Details Page](#index_split_000.html#p33)
        *   [NNI Command Line](#index_split_000.html#p37)
        *   [NNI Experiment Configuration](#index_split_000.html#p38)
        *   [Embedded NNI](#index_split_000.html#p40)
        *   [Troubleshooting](#index_split_000.html#p41)
        *   [TensorFlow and PyTorch](#index_split_000.html#p42)
        *   [Summary](#index_split_000.html#p43)
*   [Chapter 2: Hyperparameter Optimization](#index_split_000.html#p44) 
    *   [What Is Hyperparameter?](#index_split_000.html#p44) 
        *   [Layer Hyperparameter](#index_split_000.html#p48)
        *   [Training Hyperparameter](#index_split_000.html#p48)
        *   [Feature Hyperparameter](#index_split_000.html#p49)
        *   [Design Hyperparameter](#index_split_000.html#p52)
        *   [Search Space](#index_split_000.html#p53)
        *   [choice](#index_split_000.html#p54)
        *   [randomint](#index_split_000.html#p55)
        *   [uniform](#index_split_000.html#p55)
        *   [quniform](#index_split_000.html#p55)
        *   [loguniform](#index_split_000.html#p55)
        *   [qloguniform](#index_split_000.html#p56)
        *   [normal](#index_split_000.html#p56)
        *   [qnormal](#index_split_000.html#p56)
        *   [lognormal](#index_split_000.html#p56)
        *   [qlognormal](#index_split_000.html#p56)
        *   [Tuners](#index_split_000.html#p59)
        *   [Random Search Tuner](#index_split_000.html#p60)
        *   [Grid Search Tuner](#index_split_000.html#p61)
        *   [Organizing Experiment](#index_split_000.html#p61)
        *   [Optimizing LeNet for MNIST Problem](#index_split_000.html#p65)
        *   [TensorFlow LeNet Implementation](#index_split_000.html#p70)
        *   [PyTorch LeNet Implementation](#index_split_000.html#p74)
        *   [Performing LeNet HPO Experiment](#index_split_000.html#p79)
        *   [Upgrading LeNet with ReLU and Dropout](#index_split_000.html#p84)
        *   [TensorFlow LeNet Upgrade Implementation](#index_split_000.html#p88)
        *   [PyTorch LeNet Upgrade Implementation](#index_split_000.html#p91)
        *   [Performing LeNet Upgrade HPO Experiment](#index_split_000.html#p95)
        *   [From LeNet to AlexNet](#index_split_000.html#p98)
        *   [TensorFlow LeNet Evolution Implementation](#index_split_001.html#p107)
        *   [PyTorch LeNet Evolution Implementation](#index_split_001.html#p113)
        *   [Performing LeNet Evolution HPO Experiment](#index_split_001.html#p120)
        *   [Summary](#index_split_001.html#p123)
*   [Chapter 3: Hyperparameter Optimization Under Shell](#index_split_001.html#p124) 
    *   [Tuners](#index_split_001.html#p124)
    *   [Evolution Tuner](#index_split_001.html#p130)
    *   [Anneal Tuner](#index_split_001.html#p135)
    *   [Sequential Model-Based Optimization Tuners](#index_split_001.html#p141)
    *   [Tree-Structured Parzen Estimator Tuner](#index_split_001.html#p145)
    *   [Gaussian Process Tuner](#index_split_001.html#p151)
    *   [Which Tuner to Choose?](#index_split_001.html#p155)
    *   [Custom Tuner](#index_split_001.html#p157)
    *   [Tuner Internals](#index_split_001.html#p157)
    *   [New Evolution Custom Tuner](#index_split_001.html#p160) 
        *   [Early Stopping](#index_split_001.html#p169)
        *   [Median Stop](#index_split_001.html#p171)
        *   [Curve Fitting](#index_split_001.html#p175)
        *   [Risk to Stop a Good Trial](#index_split_001.html#p176)
        *   [Searching for Optimal Functional Pipeline and Classical AutoML](#index_split_001.html#p177)
        *   [Problem](#index_split_001.html#p179)
        *   [Operators](#index_split_001.html#p181)
        *   [Search Space](#index_split_001.html#p184)
        *   [Model](#index_split_001.html#p188)
        *   [Tuner](#index_split_001.html#p190)
        *   [Experiment](#index_split_001.html#p192)
        *   [Limits of HPO Applying to Neural Architecture Search](#index_split_001.html#p196)
        *   [Hyperparameters for Hyperparameter Optimization](#index_split_001.html#p196)
        *   [Summary](#index_split_001.html#p197)
*   [Chapter 4: Multi-trial Neural Architecture Search](#index_split_001.html#p198) 
    *   [Neural Architecture As Data Flow Graph](#index_split_001.html#p199)
    *   [Neural Architecture Search Using Retiarii (PyTorch)](#index_split_001.html#p200) 
        *   [Introduction to NAS Using Retiarii](#index_split_001.html#p201)
        *   [Retiarii Framework](#index_split_001.html#p209)
        *   [Base Model](#index_split_001.html#p211)
        *   [Mutators](#index_split_001.html#p212) 
            *   [LayerChoice](#index_split_001.html#p213)
            *   [ValueChoice](#index_split_001.html#p214)
            *   [InputChoice](#index_split_001.html#p214)
            *   [Repeat](#index_split_002.html#p222)
            *   [Labeling](#index_split_002.html#p225)
            *   [Example](#index_split_002.html#p226)
        *   [Evaluators](#index_split_002.html#p227)
        *   [Exploration Strategies](#index_split_002.html#p228) 
            *   [Random Strategy](#index_split_002.html#p228)
            *   [Grid Search](#index_split_002.html#p228)
            *   [Regularized Evolution](#index_split_002.html#p228)
            *   [TPE Strategy](#index_split_002.html#p231)
            *   [RL Strategy](#index_split_002.html#p231)
        *   [Experiment](#index_split_002.html#p233)
        *   [CIFAR-10 LeNet NAS](#index_split_002.html#p234)
        *   [CIFAR-10 ResNet NAS](#index_split_002.html#p249)
    *   [Classic Neural Architecture Search (TensorFlow)](#index_split_002.html#p259) 
        *   [Base Model](#index_split_002.html#p260)
        *   [Mutators](#index_split_002.html#p261)
        *   [Trial](#index_split_002.html#p263)
        *   [Search Space](#index_split_002.html#p264)
        *   [Search Strategy](#index_split_002.html#p265)
        *   [Experiment](#index_split_002.html#p265)
        *   [Summary](#index_split_002.html#p269)
*   [Chapter 5: One-Shot Neural Architecture Search](#index_split_002.html#p270) 
    *   [One-Shot NAS in Action](#index_split_002.html#p270)
    *   [Supernet Architecture](#index_split_002.html#p285)
    *   [One-Shot Algorithms](#index_split_002.html#p295)
    *   [Efficient Neural Architecture Search (ENAS)](#index_split_002.html#p295)
    *   [TensorFlow ENAS Implementation](#index_split_002.html#p304)
    *   [PyTorch ENAS Implementation](#index_split_002.html#p306)
    *   [Differentiable Architecture Search (DARTS)](#index_split_002.html#p308)
    *   [GeneralSupernet Solving CIFAR-10](#index_split_002.html#p313)
    *   [Training GeneralSupernet Using TensorFlow and ENAS](#index_split_002.html#p316)
    *   [Training GeneralSupernet Using PyTorch and DARTS](#index_split_003.html#p323)
    *   [HPO vs. Multi-trial NAS vs. One-Shot NAS](#index_split_003.html#p330)
    *   [Summary](#index_split_003.html#p331)
*   [Chapter 6: Model Pruning](#index_split_003.html#p332) 
    *   [What Is Model Pruning?](#index_split_003.html#p332)
    *   [LeNet Model Pruning](#index_split_003.html#p335)
    *   [One-Shot Pruners](#index_split_003.html#p342)
    *   [Pruner Configuration](#index_split_003.html#p346)
    *   [Level Pruner](#index_split_003.html#p347)
    *   [FPGM Pruner](#index_split_003.html#p350)
    *   [L1Norm and L2Norm Pruners](#index_split_003.html#p353)
    *   [Iterative Pruners](#index_split_003.html#p355)
    *   [Linear Pruner](#index_split_003.html#p356)
    *   [AGP Pruner](#index_split_003.html#p357)
    *   [Iterative Pruner Configuration](#index_split_003.html#p358)
    *   [Iterative Pruning Scenarios](#index_split_003.html#p359)
    *   [Best Accuracy Under Size Threshold Scenario](#index_split_003.html#p360)
    *   [Minimal Size Above Accuracy Threshold Scenario](#index_split_003.html#p364)
    *   [Summary](#index_split_003.html#p368)
*   [Chapter 7: NNI Recipes](#index_split_003.html#p369) 
    *   [Speed Up Trials](#index_split_003.html#p369)
    *   [Start–Stop–Resume](#index_split_003.html#p370)
    *   [Continue Finished Experiment](#index_split_003.html#p371)
    *   [NNI and TensorBoard](#index_split_003.html#p371)
    *   [Move Experiment to Another Server](#index_split_003.html#p375)
    *   [Scaling Experiments](#index_split_003.html#p376)
    *   [Shared Storage](#index_split_003.html#p379)
    *   [One-Shot NAS with Checkpoints and TensorBoard](#index_split_003.html#p381)
    *   [Summary](#index_split_003.html#p389)
*   [Index](#index_split_003.html#p390)