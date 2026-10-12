
![](images/cover.jpg)

![Cover](images/cover.jpg)

Copyright © 2024 BPB Online

*All rights reserved.* No part of this book may be reproduced, stored in a retrieval system, or transmitted in any form or by any means, without the prior written permission of the publisher, except in the case of brief quotations embedded in critical articles or reviews.

Every effort has been made in the preparation of this book to ensure the accuracy of the information presented. However, the information contained in this book is sold without warranty, either express or implied. Neither the author, nor BPB Online or its dealers and distributors, will be held liable for any damages caused or alleged to have been caused directly or indirectly by this book.

BPB Online has endeavored to provide trademark information about all of the companies and products mentioned in this book by the appropriate use of capitals. However, BPB Online cannot guarantee the accuracy of this information.

First published: 2024

Published by BPB Online

WeWork

119 Marylebone Road

London NW1 5PU

**UK | UAE | INDIA | SINGAPORE**

ISBN 978-93-55515-353

[www.bpbonline.com](https://www.bpbonline.com)

**Dedicated to**

All the people who are changing the world through technology

# About the Author

**Hemanth Kumar K** has more than decade of experience in the corporate industry, started his career in telecom domain worked on multiple projects and clients across the globe to plan and optimize mobile networks. Got fascinated towards data & machine learning changed his focus and career path towards data science & analytics. He has worked on many data analytics projects to solve business problems in various domains such as insurance, telecom, media, health, engineering analytics. In addition to `GCP` he has also worked on `Azure` platform.

# About the Reviewers

*   ❖ **Dr. Muthu Kumaraswamy B** is an Associate Director at `Searce` where he leads a team of 100+ Machine learning engineers and delivers custom machine learning solutions. He has over 15 years of experience in the IT industry, and has worked on a variety of projects in the areas of software development, cloud computing, and artificial intelligence. He has a Ph.D. from the University Madras.

    Dr. Muthu Kumaraswamy is an expert in a variety of programming languages, including `JavaScript`, `Python`, and `C++`. He is also proficient in a variety of cloud computing platforms, including `Google Cloud Platform` and `Amazon Web Services`. He is a strong advocate for using artificial intelligence to solve real-world problems, and has developed several AI-powered solutions for his clients.

    Dr. Muthu Kumaraswamy is a frequent speaker at industry conferences and events. He is also a regular contributor to technical blogs and publications. He is passionate about sharing his knowledge and expertise with others, and is always looking for new ways to help people learn and grow.

    Here are some of his notable achievements:

*   Developed a cloud-based AI solution that helped a large manufacturing company improve its production efficiency by 15%.

*   Led a team of engineers in the development of a new Machine learning platform that was used by a financial services company to automate its risk management processes.

*   Published several articles in technical journals and magazines on the topics of software development, cloud computing, and artificial intelligence.

*   Presented at several industry conferences on the use of AI to solve real-world problems.

*   Dr. Muthu Kumaraswamy is a highly skilled and experienced Machine learning engineer with a proven track record of success in delivering high-quality solutions to his clients. He is a valuable asset to any team and would be a great addition to your company

*   ❖ **Abdul Hannan Siddiqui** is a Passionate and Innovative Machine Learning Engineer with over 5 years of experience in `MLOps`, Time Series, Predictive Modeling, Computer Vision, and Natural Language Processing. He is a `Google Certified Machine Learning Engineer` with multiple `Google Cloud Platform` certifications, specializing in Data Engineering using `Python`, `ETL`, and effectively handling large-scale migration processes to the cloud, as well as data analytics on `Google BigQuery`.

    Abdul Hannan Siddiqui is currently working as a Senior Machine Learning Engineer at `Argility`. Prior to that, he worked as a Machine Learning Engineer at `Quantiphi` and as a Data Engineer at `Accenture`. His expertise lies in `MLOps`, Time Series, Predictive Modeling, Computer Vision, and Natural Language Processing, and he is highly skilled in using `Python` for Data Engineering and `ETL` processes. With his extensive experience and `Google Cloud Platform` certifications, Abdul Hannan Siddiqui is dedicated to leveraging his skills to drive successful machine learning and data science projects, ensuring optimal outcomes for his clients or organization.

# Acknowledgements

I want to sincerely thank my family and friends for their continuous support and inspiration as I wrote this book.

I’m also appreciative of `BPB Publications` for their advice and know-how in helping me finish this book. This book had a lengthy revision process that benefited greatly from the participation and cooperation of editors, technical specialists, and reviewers.

Throughout my many years in the corporate industry, I would also like to recognize the important contributions of my coworkers and colleagues, who have taught me a lot and given me insightful criticism of my work.

Finally, I want to express my gratitude to all the readers who have shown interest in and support for my work. Your words of support have been

# Preface

In today’s world data enthusiast are expected to have expertise in one more cloud platforms. Solving business problems through data on cloud requires comprehensive understanding not just of algorithms but also cloud platforms and its components.

This book aims in helping you understand `Vertex AI` component of `Google Cloud Platform (GCP)` with real time examples. Before diving into `Vertex AI`, book gives you fair idea about google cloud platform and its components and also the positioning of `Vertex AI`. For all the examples used in this book for model training data is either uploaded to `google cloud storage (GCS)` or `big query`, so we will start with `GCS`, `big query` and also about the `Identity access and management (IAM)`. `Vertex AI` has lot of components starting from datasets, `Workbench`, `Pipelines`, training, experiments, models, end points and features. The primary objective here is to learn these features of `Vertex AI` concepts with real-time use cases.

[Chapter 1: Basics of Google Cloud Platform](#ch01.xhtml): starts with a fundamental understanding of `Google Cloud Platform` in this chapter. `GCP`’s footprint, hierarchy, and platform, as well as how we can interact with `GCP`’s components. `GCP`’s several cloud service models (`IAAS`, `PAAS`, `SAAS`). A high-level overview of `GCP`’s various components. We also take a look at `GCP`’s storage capabilities, including how to set up `Google Cloud storage` and upload files to it. How to use `Google`’s `Big Query`. We will comprehend the necessity and significance Incident and Access Management (`IAM`) in the platform.

[Chapter 2: Introduction to Vertex AI and AutoML Tabular](#ch02.xhtml): In this chapter, the `GCP Vertex AI` component will be discussed. The integration of `automl` and custom model features into a single `GCP` component. We also comprehend the key distinctions between `automl` and custom models. We’ll start with a walkthrough of how to create a dataset for structural data and how to train an `automl` model for it. We’ll look at how to deploy the model and get batch and online predictions.
