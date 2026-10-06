
# CHAPTER 20 WHEN SIZE MATTERS: SCALABILITY AND THE CLOUD

the comprehensive machine learning service Amazon SageMaker that supports everything from data prep to model training and deployment. It also integrates the popular frameworks PyTorch and TensorFlow for neural nets. Other tools do not require much coding, like Amazon Comprehend for NLP, Amazon Lex for building chatbots, and Amazon Rekognition for video-based work.

In the world of compute, Amazon EC2 is the classic choice, allowing you to run virtual servers. Amazon Linux allows you to spin up Linux-based environments. Amazon Lambda offers serverless computing triggered by events. AWS Batch allows you to run large batch jobs without having a lot of infrastructure to manage.

AWS also has a lot of developer tools, including AWS App Studio for internal applications, AWS CodeBuild for writing and testing code, and several tools related to specific languages.

# Google Cloud

Google launched a preview of Google App Engine in 2008, allowing people to create web apps that could easily scale. It came out of preview in 2011 and became one of the major cloud platform providers, now offering over 150 products and services, which you can find on their list of products.⁶

BigQuery is a data warehouse that can be used for many things, including analytics. Cloud Storage supports object storage for unstructured data like images and videos, and Filastore provides fully managed file storage for network file systems used in enterprise applications. Cloud SQL supports three flavors of relational databases as well as some other options for SQL Server and PostgreSQL. There are also NoSQL options, Datastore and Spanner, and Cloud Bigtable. Dataform allows you to run SQL workflows in BigQuery.

> ⁶https://cloud.google.com/products/

There are a handful of products that can be used for ETL in Google Cloud, including Cloud Data Fusion and Datastream. Cloud Data Fusion is a fully managed tool that lets users build, manage, and schedule ETL through a visual interface. Datastream is a change data capture and replication service that enables moving data between databases and storage services.

Another important tool is Dataplex, which helps to manage data even if it's spread out in silos. Spanner allows you to bring several types of databases together, including relational and NoSQL.

In the analytics space, BigLake unifies data from data lakes and warehouses for analytics, and Dataflow is a serverless stream and batch processing tool with ETL and real-time analytics in mind. Document AI allows for NLP work, and Recommendations AI is a recommendation engine. Vertex AI is a general-purpose analytics and AI platform with several specific offerings, including an agent builder.

In the compute space, there are several useful tools. Dataproc controls Spark and Hadoop clusters allowing for work with big data. Compute Engine allows the running of customizable VMs. There are also other tools for compute for specific needs, including Cloud GPUs (for heavy-duty processing and ML training) and Cloud TPUs (for accelerated neural net computations). Cloud Workstations allows for serverless deployment of containerized applications, and App Engine provides a serverless platform for hosting web apps. They also offer Kubernetes-based serverless capabilities through Knative.

# Key Takeaways and Next Up

In this chapter, we talked about the cloud and scalability and everything that ties into that world. This included understanding the differences between the on-prem data centers of yesterday and modern cloud computing and the scalability, elasticity, resource pooling, and paying only for what you need and use. We talked about big data and the importance of scalability. We also addressed distributed and parallel computing, both important in improving computation time of large-scale jobs. Lastly, we looked at the three major cloud platforms and some of what they have to offer.

In the next chapter, we'll be taking a deep dive into data science project management first by understanding traditional project management and modern software development management. We'll give an overview of a Kanban approach to managing data science projects. We'll also talk about post-project steps.

# PRACTITIONER PROFILE: BHUMIKA SHAH

**Name:** Bhumika Brijen Shah

**Current Title:** Container technology engineering manager

**Current Industry:** Retail

**Years of Experience:** 17 years in tech, including 3 as a data analyst, 7 years in cloud DevOps, and 4 in platform solutions

**Education:**

- Certifications in Kubernetes, Azure, and Google Cloud Platform
- Postgraduate in Computer Science
- Bachelor’s in Computer Science

The opinions expressed here are Bhumika’s and not any of her employers', past or present.

# Background

As a teenager, Bhumika loved computers and formally studied computer science in school. The next logical step was to get an undergrad degree in computer science, which she did. She did an internship while still in university, where she learned about software engineering, doing testing and other important steps. She started to develop a real software developer mindset there. She got her master’s in computer science, too, and kept taking courses to continue to grow.

# Work

Her first job was an ETL developer (extract, transform, load—basically moving data from one place to another), which is where she first really encountered “data” as a thing in business. She loved how valuable the transformation step could be, taking something hard to use and making it useful. She moved into a data analyst role and continued to grow her data skills. She enjoyed the visualization and how it enabled her to show things that were difficult to see in the data. She continued this path toward data science, learning about data obfuscation, and then she became interested in data security, which led to another small shift in her career. She moved into a cloud DevOps role, where she was developing infrastructure and solutions doing actions. She loved scripting all of that. She grew in that area before moving into container platform engineering, where she now manages a team.

# Sound Bites

**Favorite Parts of the Job:** Bhumika loves the problem-solving aspect of all the jobs she's done, as well as constantly learning. She also loves collaborating with different teams and making solutions work. She especially enjoys creating solutions that are scalable.

**Least Favorite Parts of the Job:** Trying to balance competing priorities can be frustrating. As a manager, she has to make sure all of her team's work aligns with company goals and vision but still make stakeholders happy. This can be hard at times. One thing that can be frustrating is when other people make decisions about things you need to do for your work.

**Favorite Project:** One project she liked was to create a secure and scalable Kubernetes environment that would improve deployment time. She was able to reduce deployment time by 40%, which helped developers avoid downtime. This was especially useful to data scientists because they are starting to use Kubernetes. This gives them data tools, including ones to obfuscate their data. Some of the aspects of the project that were interesting were the autoscaling, optimization, reducing operational costs, and being able to migrate monolithic tools to microservices.

**Skills Used Most:** Problem-solving, critical thinking, communication, leadership, and her technical expertise, in that order

**Primary Tools Used Currently:** Kubernetes, Terraform, Jenkins CI/CD pipelines, cloud services (GCP and Azure), Golang, and SQL

Future of Cloud: All industries are moving toward cloud computing and automation. This makes it easier for everyone to deploy applications and AI tools are being used as part of the cloud and automation tools and as part of the applications being deployed.

**What Makes a Good Technology Professional:** Curiosity and creativity with strong technical skills. A solid understanding of statistics. Communicating at the right time (not too soon, not too late). They also need to know how to benefit from AI tools—know what you're trying to get out of it rather than using it willy-nilly.

**Her Tip for Prospective Technology Professionals:** Go to open houses to meet people and learn about companies and the kinds of roles out there. Then focus on building strong technical foundations in whatever area you intend to focus on.

Bhumika is a container platform engineering manager with a varied background in data and other technologies.
