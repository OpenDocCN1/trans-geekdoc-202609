
xviii

Contents

## Chapter 22 Analyzing Outcome-Based Education Using Multicriteria Decision-Making................299
Sathish Kumar Kumaravel, Regan Murugesan, Nagadevi Bala Nagram, Kala Raja Mohan, and R. Narmada Devi

- 22.1 Introduction...............................................................................................................299
- 22.2 Standard Definitions...............................................................................301
- 22.2.1 Attributes......................................................................................301
- 22.2.2 Criteria........................................................................................301
- 22.2.3 Decision Matrix...............................................................................301
- 22.2.4 Normalized Decision Matrix...............................................................301
- 22.2.5 Weighted Normalized Decision Matrix..................................................301
- 22.2.6 TOPSIS Score................................................................................301
- 22.2.7 Ranking...........................................................................................302
- 22.3 The Outranking Algorithm...............................................................302
- 22.4 The TOPSIS Algorithm...........................................................................302
- 22.5 Conclusion...........................................................................................305
References...............................................................................................305

## Chapter 23 Selecting a Best Professor Awardee Using Multicriteria Decision-Making...............................................................307
Kala Raja Mohan, R. Narmada Devi, Nagadevi Bala Nagram, Regan Murugesan, and Sathish Kumar Kumaravel

- 23.1 Introduction...............................................................................................308
- 23.2 Standard Definitions...............................................................................308
- 23.2.1 Attributes......................................................................................308
- 23.2.2 Criteria........................................................................................308
- 23.2.3 Decision Matrix...............................................................................309
- 23.2.4 Normalized Decision Matrix...............................................................309
- 23.2.5 Variance.......................................................................................309
- 23.2.6 Weighted Normalized Matrix...............................................................309
- 23.2.7 Concordance Matrix................................................................309
- 23.2.8 Discordance Matrix................................................................309
- 23.2.9 Pure Concordance Index...............................................................309
- 23.2.10 Pure Discordance Index...............................................................310
- 23.2.11 Ranking Table..............................................................................310
- 23.3 Methodology...............................................................................310
- 23.4 MCDM Results and Discussion...........................................................310
- 23.5 Results and Discussion................................................................313
- 23.6 Conclusion...............................................................................313
References...............................................................................................314

Contents xix

## Chapter 24 Predicting Lumpy Skin Disease Using Machine Learning ........... 317
Nagadevi Bala Nagaram, R. Marmada Devi, Kala Raja Mohan, Sathish Kumar Muravavel, and Regan Murugesan

- 24.1 Introduction ..................................................................... 317
- 24.2 Characteristics of Lumpy Skin Disease ................................ 318
- 24.2.1 LSD Transmission Routes ................................................... 318
- 24.2.2 Factors Influencing Transmission ........................................ 318
- 24.2.3 Prevention and Control Measures ...................................... 319
- 24.3 Problem Statement .......................................................... 319
- 24.3.1 Supervised Education ....................................................... 319
- 24.3.2 Unsupervised Learning ............................................... 320
- 24.4 The Model Development Hierarchy ....................................... 320
- 24.5 The LSD Prediction Model ................................................ 321
- 24.6 Results and Discussion ................................................ 323
- 24.7 Conclusion ..................................................................... 325
- References ....................................................................... 325
- Author Index. .................................................................. 327
- Subject Index ................................................................... 329

![](img/62c36bee0e5ae6b397770e7de372b0e7_20_0.png)

# Preface

In the dynamic landscape of engineering and decision-making, integrating multi-criteria analysis with machine learning technologies has emerged as a pivotal paradigm for optimizing solutions across diverse domains. This book, *Multi-Criteria Decision-Making and Optimum Design with Machine Learning: A Practical Guide*, is a testament to the relentless pursuit of innovation and excellence within this evolving field.

This comprehensive volume, spanning twenty-four chapters authored by esteemed researchers and practitioners, encapsulate a wealth of knowledge and practical insights aimed at advancing decision-making methodologies. The authors of each chapter delve into unique facets of decision-making optimization, from the intricate exploration of fuzzy systems to the application of machine learning in optimizing topological parameters. The collaborative efforts of the contributing authors, under the editorial guidance of Van Thanh Nguyen, Van-Thuc Nguyen, Tht M. Vo, and Van-Chinh Truong, resulted in a panoramic view of research that traverses disciplines, from engineering design to sustainable development. This interdisciplinary approach underscores the significance of leveraging innovative methodologies to address complex decision-making challenges in real-world scenarios.

As readers embark on this intellectual journey, they will encounter a diverse array of topics, from optimizing surface roughness in machining processes to identifying better teachers using advanced algorithms. Each chapter is a testament to the authors' ingenuity and dedication to pushing the boundaries of knowledge and practice. Moreover, including practical case studies and real-world applications ensures that this book transcends theoretical discourse, offering actionable insights that can inform navigating the intricacies of destination decision-making dilemmas using machine learning, the methodologies elucidated in these chapters hold immense potential for driving tangible outcomes and fostering sustainable.

In conclusion, *Multi-Criteria Decision-Making and Optimum Design with Machine Learning: A Practical Guide* represents a seminal contribution to the burgeoning field of decision science. We sincerely hope this volume will inspire researchers, practitioners, and students to embark on their own explorations, armed with the knowledge and tools necessary to tackle the complex challenges of the modern world, and we highly appreciate all our readers.

The Editorial Team

![](img/62c36bee0e5ae6b397770e7de372b0e7_22_0.png)

# About the Editors

Van Thanh Tien Nguyen (member, IEEE) received master’s degrees in mechanical engineering and linguistics from Viet Nam National University Ho Chi Minh City, Bach Khoa University, and HCMC University of Social Sciences and Humanities in 2012 and 2020, respectively. He holds a Ph.D. in industrial engineering and management from the National Kaohsiung University of Science and Technology, Taiwan. He has published over 66 journals and conference papers, with 101 review reports, and is an academic reviewer for several journals. He has experience studying and working in labs as a researcher in many countries, such as South Korea, Thailand, Russia, and Taiwan. He is a lecturer at the Industrial University of Ho Minh City, Vietnam. His areas of interest are machine learning (AI), compliant mechanisms design, numerical computation, multicriteria decision-making, and supply chain management. Dr. Nguyen’s works have significantly influenced his field, as evidenced by Scopus H-index of 19 and 748 citations (as of 2024).

Nhut T.M. Vo (member, IEEE) is a versatile professional. She received the M.Sc. degree from the National Kaohsiung University of Science and Technology, Taiwan, where she is currently pursuing a Ph.D. in industrial engineering and management. Her professional journey has taken through various sectors, including banking, the jewelry industry, information technology, and e-commerce, enriching her understanding of different industries. She is also a self-published author with books about lean management and other fields. Her research interests span various topics, including the Internet of Things, blockchain, cloud computing, machine learning (AI), green energy, logistics, e-commerce, and numerical computation.

Vinh Truong is not just a member of the Faculty of Mechanical Engineering at the Industrial University of Ho Minh City, Vietnam, but a dedicated educator. Truong has also been involved in research and academia, participating in several research projects. He has successfully developed and implemented technologies, significantly contributing to the industry, but his true passion lies in inspiring and educating future generations of engineers, a commitment that shines through his work and contributions to the field of mechanical engineering.

Van-Thuc Nguyen is a lecturer at Ho Chi Minh University of Technology and Education in Vietnam. He has a Ph.D. from the National Kaohsiung University of Science and Technology, Taiwan, and has published over 50 SCIE journal papers. His areas of expertise include manufacturing material science and mechanical processing. He is a highly respected researcher and educator in his field.
