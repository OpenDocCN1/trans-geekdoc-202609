
1. [三种负载均衡策略](#f_0066.xhtml#d24e22080)

2. [在 gRPC 中于客户端进行负载均衡](#f_0067.xhtml#d24e22163)

3. [使服务器可发现](#f_0068.xhtml#d24e22301)

4. [解决服务器问题](#f_0069.xhtml#d24e22813)

5. [使用选择器路由并平衡请求](#f_0070.xhtml#pickers)

6. [测试端到端的发现和均衡](#f_0071.xhtml#d24e24530)

7. [你学到了什么](#f_0072.xhtml#d24e24722)

6.  [第四部分. 部署](#f_0074.xhtml#d24e24730) 

    1.  [本地使用 Kubernetes 部署应用程序（第 10 章）](#f_0075.xhtml#deploychapter) 

        1.  [什么是 Kubernetes？](#f_0076.xhtml#d24e24761)

        2.  [安装 kubectl](#f_0077.xhtml#d24e24816)

        3.  [使用 Kind 进行本地开发和持续集成](#f_0078.xhtml#d24e24895)

        4.  [编写代理命令行接口](#f_0079.xhtml#d24e25019)

        5.  [构建 Docker 镜像](#f_0080.xhtml#d24e25872)

        6.  [使用 Helm 配置并部署服务](#f_0081.xhtml#d24e26012)

        7.  [在完全限定域名上广告 Raft](#f_0082.xhtml#d24e27859)

        8.  [你学到了什么](#f_0083.xhtml#d24e28418)

    2.  [11\. 使用 Kubernetes 将应用程序部署到云端](#f_0084.xhtml#cloudchapter) 

        1.  [创建 Google Kubernetes Engine 集群](#f_0085.xhtml#d24e28495)

        2.  [使用 Metacontroller 创建自定义控制器](#f_0086.xhtml#d24e28750)

        3.  [部署到 Internet 上](#f_0087.xhtml#d24e29727)

        4.  [你学到了什么](#f_0088.xhtml#d24e29782)

Copyright © 2021, The Pragmatic Bookshelf. 

# Early Praise for Distributed Services with Go

Having built most of the technologies in this book without the benefit of this book, I can wholeheartedly recommend Distributed Services with Go. Travis delivers years of practical experience distilled into a clear and concise guide that takes the reader step by step from foundational knowledge to production deployment. This book earns my most hearty endorsement.

| → || Brian Ketelsen |

| --- | --- |

|  || Principal Developer Advocate, Microsoft; and Organizer, GopherCon |

In this practical, engaging book, Travis Jeffery shines a light on the path to building distributed systems. Read it, learn from it, and get coding!

| → || Jay Kreps |

| --- | --- |

|  || CEO, Confluent, Inc., and Co-Creator of Apache Kafka |

Travis Jeffery distills the traditionally academic topic of distributed systems down to a series of practical steps to get you up and running. The book focuses on the real-world concepts used every day by practicing software engineers. It’s a great read for intermediate developers getting into distributed systems or for senior engineers looking to expand their understanding.

| → || Ben Johnson |

| --- | --- |

|  || Author of BoltDB |

For any aspiring Gopher, Travis provides a gentle introduction to complex topics in distributed systems and provides a hands-on approach to applying the concepts.

| → || Armon Dadgar |

| --- | --- |

|  || HashiCorp Co-Founder |

A must-have for Gophers building systems at scale.

| → || William Rudenmalm |

| --- | --- |

|  || Lead Developer, CREANDUM |

This book is a great resource for Go developers looking to build and maintain distributed systems. It pairs an incremental development process with extensive code examples to teach you how to write your own distributed service, understand how it works under the hood, and how to deploy your service so others may start using it.

| → || Nishant Roy |

| --- | --- |

|  || Tech Lead |

#   

Acknowledgments

I write this, having finished the book, two and a half years after I began. Writing this book was the hardest thing I’ve done. I’ve built a few startups and several open source projects—this was much harder. I set out to write a good book people would enjoy and find useful. I’m critical of myself and my work and wouldn’t put out anything I didn’t deem worthy. It took me a long time to write because I didn’t want to compromise. I’m happy with this book and proud of myself.

I thank my editors, Dawn Schanafelt and Katharine Dvorak, for their patience and for helping me to improve my writing and motivating me in hard times.

Thank you to my publisher, The Pragmatic Bookshelf, for the guidance I received in writing my first book and for all of the work out of view.

I thank my book’s reviewers and beta readers for giving me their impressions of the book and contributing suggestions and errata to help me improve the book. Thank you to Clinton Begin, Armon Dadgar, Ben Johnson, Brian Ketelsen, Jay Kreps, Nishant Roy, William Rudenmalm, and Tyler Treat.

Thank you to the free and open source software communities for putting out code to study, change, and run. Special thanks to the people at Hashicorp for open-sourcing their Raft and Serf packages I use in this book and their services like Consul, whose source I studied and learned from a lot. Thank you to the Emacs and Linux contributors—the text editor and operating system I wrote this book with. Thank you to the Go team for creating a simple, stable, useful language.

Thank you to my parents, Dave and Tricia Jeffery, for buying my first computer and programming books and encouraging me with a strong work ethic.

Thank you to my high school English teacher, Graziano Galati, for giving me the right reading at the right time in my life.

Thank you to J. R. R. Tolkien for authoring The Lord of the Rings. I read it while writing this book, and the rapport with Frodo and Samwise aided me on the journey.

I thank my cat, Callie Jeffery. I adopted her a quarter of the way through writing the book, and her useful contributions to the discussion helped speed up my writing pace.

Thank you to Emily Davidson for her love and support and for fueling me with broccoli soup, ginger kombucha, and matcha tea.

Thank you, dear reader, for independently furthering your skills and knowledge and having the ambition to put your dent in the universe.

—Travis Jeffery

Copyright © 2021, The Pragmatic Bookshelf. 

#   

Introduction

Go has become the most popular language for building distributed services, as shown by projects like Docker, Etcd, Vault, CockroachDB, Prometheus, and Kubernetes. Despite the number of prominent projects such as these, however, there’s no resource that teaches you why or how you can extend these projects or build your own.

Where do you begin if you want to build a distributed service?

When I began learning how to build distributed services, I found the existing resources to be of two extremes:

*   Concrete code—distributed services are large, complex projects, and the prominent ones have had teams working on them for years. The layout of these projects, their technical debt, and their spaghetti code bury the ideas you’re interested in, which means you have to dig them out. At best, learning from code is inefficient. Plus there’s the risk that you may uncover outdated and irrelevant techniques that you’re better off avoiding in your own projects.

*   Abstract papers and books—papers and books like Designing Data-Intensive Applications by Martin Kleppmann^([\[1\]](#f_0008.xhtml#FOOTNOTE-1)) describe how the data structures and algorithms behind distributed services work but cover them as discrete ideas, which means you’re left on your own to connect them before you can apply them in a project.

These two extremes leave a chasm for you to cross. I wanted a resource that held my hand and taught me how to build a distributed service—a resource that explained the big ideas behind distributed services and then showed me how to make something of them.

I wrote this book to be that resource. Read this book, and you’ll be able to build your own distributed services and contribute to existing ones.

## Who This Book Is For

