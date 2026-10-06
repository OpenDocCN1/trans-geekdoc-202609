
- 12.9 Sustaining High-Performance Teams 431
- 12.10 Main Takeaways 433
- 12.11 Exercises 436
- 12.12 References 438

## 13 Communicating Effectively 443

- 13.1 VSN-C for Structuring Communications 446
- 13.2 Winston Star: Essentials for Being Remembered 448
- 13.3 Essentials of Outlining 451
- 13.4 Writing and Presentation Fundamentals 453
- 13.5 Main Takeaways 463
- 13.6 Exercises 464
- 13.7 References 465

## PART III HUMAN-MACHINE AUGMENTATION: USE CASES

## 14 Use-Case Example 1: Misty Companion Robot as Alzheimer's Application 469

- 14.1 Exercises 475
- 14.2 References 476

## 15 Use-Case Example 2: Bose AI-Powered Cycling Coach and Warning System 477

- 15.1 Exercises 483
- 15.2 Reference 483

## 16 Use-Case Example 3: Meal Evaluation and Attainment Logistics System (MEALS) 485

- 16.1 Exercises 492

## 17 Use-Case Example 4: Managing Energy for Smart Homes (MESH) 493

- 17.1 Exercises 499
- 17.2 References 499

## 18 Use-Case Example 5: AquaAI, an AI-Powered Modernized Marine Maintenance System

- 18.1 Exercises 506
- 18.2 Reference 507

## Appendix 509

- A.1 Representative AI Industries and Sample Applications 509
- A.2 Setting up Your Interactive Development Environment (for PC or Mac OS Operating Systems) 510
- A.3 ML Performance Metrics 512
- A.4 Multilayer Perceptron Algorithm 517
- A.5 CNN with MNIST Fashion Data Set 521
- A.6 Raspberry Pi: Introduction and Setup 524

## Abbreviations 525

## Index 529

## Preface

This book provides a comprehensive introduction to a systems approach to the architecture, design, development, and deployment of artificial intelligence (AI) capabilities. Readers will gain insights into seven areas:

- Understanding an end-to-end AI system architecture
- Learning the technical underpinnings of the AI pipeline building blocks
- Formulating a strategic vision and development road map focused on AI products and services
- Transitioning of AI developments into operations
- Fostering and leading innovative AI teams
- Communicating effectively the AI value proposition to stakeholders
- Receiving practical experience from use cases, exercises, and a large body of references

The book is intended for advanced undergraduates and graduate students, as well as working AI practitioners.

The book is divided into three parts. Part I focuses on the AI system architecture and its functional building blocks. Part II builds on the architecture principles to help formulating a strategic development plan or blueprint. The blueprint employs a development model used extensively by the authors in real-life applications. Part III concludes with a set of use cases stemming from courses taught by the authors at the Massachusetts Institute of Technology (MIT), both at the graduate level and for professionals.

We decided to write this book because there are very limited resources that address a broad treatment of AI technologies, the processes necessary for successful AI implementations and deployments, and the importance of AI talent (meaning people) to these efforts. This triad of technologies, processes, and people is paramount to the successful design, development, and deployment of AI systems. Unfortunately, many businesses fail at transitioning AI concepts and initial prototypes into operations because they lack the tools and techniques to do so. This book provides a reference source that can address challenges in transitioning AI capabilities from the development stage to useful AI products or services.

Those readers with limited knowledge of the AI building blocks are encouraged to start with part I of the book. For those readers with an AI background who want to learn about practical tools and techniques in leading AI teams from architecture principles to deployment can start with part II. The use cases discussed in part III help cement the concepts discussed in parts I and II. The large number of figures, exercises, and references complement the discussion in each chapter.

Appendix A.1 presents representative AI industries and sample applications. This list can be used in the classroom to help students with choosing areas for developing a strategic map as part of a class project. Appendices A.2–A5 provide guidelines for setting up the Anaconda environment to run a set of Jupyter notebooks, illustrating the implementation of a multilayer perceptron (MLP), a convolutional neural network (CNN), and using key machine learning (ML) performance. The description in appendices A.2–A5 are adapted from an excellent book by Aurlien Geron, Hands-On Machine Learning with SciKit, Keras and TensorFlow, 2nd edition, O'Reilly (2019). The reader can find example code and quick start instructions at https://github.com/ageron/handson-ml2. In Appendix A.6, we provide a short overview of the Raspberry Pi used in one of our MIT classes, which the students used to do a demonstration of ML neural networks to a panel of AI industry and academic experts.

The potential of AI is enormous, but it also poses significant risks if not managed properly. We hope the readers of this book adopt a systems approach—from architecture principles to deployment—to minimize the danger of AI falling outside the "guards."

As stated in the now famous Amara's Law:

> We tend to overestimate the effect of a technology in the short run and underestimate the effect in the long run.
> Roy Amara, American researcher, scientist, and futurist

As AI continues to advance, we can expect it to increasingly augment human capabilities. However, we must proceed with caution as we architect, design, develop, and deploy these capabilities by establishing rigorous testing, verification, and validation methodologies with the stakeholders in the process.

## Acknowledgments

This book had been in progress for several years. The original work dates back to when one of the authors, David Martinez, began to formulate tutorial material on artificial intelligence (AI) at MIT Lincoln Laboratory. This tutorial material served as the background and introduction to a comprehensive AI study performed at Lincoln Laboratory and by David Martinez, Bill Strelein, and Nick Malyska. Brad Dillman contributed to the organization of the AI study and all its graphics.

The book would not have been possible without the continued support of the leadership at Lincoln Laboratory. Eric Evans and Scott Anderson provided continuous encouragement and support from the beginning to the final book's completion. Jim Ward, chair of the Lincoln Laboratory Book Series (LLS), was also instrumental in encouraging us to write the book as part of the LLS. We also want to thank the leadership in the Cyber Security and Information Division (division 5) at Lincoln Laboratory for their continuing encouragement. Some of the material in part II of the book, on strategic planning and leadership, stems from years of applying these concepts in practice within division 5. Brad Dillman converted all the original lecture charts into the required book format. We also want to thank the division 5 administrative support staff, Kimberly Pitko and Renee Gylphe. Pitko served as the administrative assistant during the book's proposal preparation and facilitated access to much of the referenced material.

We also want to thank Bob Hall in the Knowledge Services Department at MIT Lincoln Laboratory, who diligently searched a large body of references at the authors' request. This book covers a broad range of topics, narrowing the search to the most relevant material for each chapter in the book was a major effort.

It has been a great pleasure to work closely with Elizabeth Swayze and Matthew Valades of the MIT Press. They provided clear and concise guidance from the start of the book's proposal stage and throughout the feedback from anonymous reviewers. We also want to thank the anonymous reviewers for their input, which made the book much stronger in terms of quality, content, and fluidity.
