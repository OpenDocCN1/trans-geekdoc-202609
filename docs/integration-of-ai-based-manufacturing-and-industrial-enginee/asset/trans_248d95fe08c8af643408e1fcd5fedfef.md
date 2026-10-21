

![](img/3d190e19625a7567e7b93c8e95b18d9c_149_0.png)

图 8.9 应用统计信息。

![](img/3d190e19625a7567e7b93c8e95b18d9c_149_1.png)

图 8.10 应用内存使用情况。

## 8.6.1 应用 1：DownTube：YouTube 视频/音频下载器

DownTube 是一款基于人工智能的应用，用于下载 YouTube 中的视频/音频内容。该应用已使用自动化系统 PhasedJS 进行部署，其部署所花费的时间如图 8.8 所示。

![](img/3d190e19625a7567e7b93c8e95b18d9c_150_0.png)

图 8.11 手动部署应用统计信息。

除了部署应用所花费的时间外，使用 PhasedJS 部署应用时还记录了各种其他统计参数值。记录的结果（如内存使用量、RSS、heapTotal、heapUsed、external 和 arrayBuffers）如图 8.9 和图 8.10 所示。

在手动部署中，很明显，如果没有适当的优化和资源供给，应用的 CPU 使用率远高于自动化部署。通过分析手动和自动化系统产生的结果，可以明显看出，CPU 使用率约为手动方法的 2 倍。内存使用量也很高（在空闲状态下，即服务器未接收任何请求时）。我们比较了这些数据，发现 PhasedJS 将内存使用量优化了 1.3 倍（在空闲和多个并行传入请求的情况下均如此）。基于 AI 的 DownTube 应用已手动部署，其统计参数和内存使用量的结果分别如图 8.11 和图 8.12 所示。

由于 PhasedJS 已优化应用配置，与手动方法相比，CPU 使用率相对较低。

## 8.6.2 应用 2：肥料推荐

肥料推荐系统是一个重量级人工智能应用，旨在为特定作物和季节推荐合适的肥料。该应用也已使用所提出的 PhasedJS 系统和手动方式分别进行了部署。

```
49.970800000000004 % Memory Usage {
  rss: 54306201.6,
  heapTotal: 28549545.984,
  heapUsed: 14833178.216,
  external: 4301431.0430000005,
  arrayBuffers: 57722.226
}
76.85040000000001 % Memory Usage {
  rss: 54334935.04,
  heapTotal: 28549545.984,
  heapUsed: 14848195.928,
  external: 4301431.0430000005,
  arrayBuffers: 57722.226
}
50.692400000000006 % Memory Usage {
  rss: 54340681.728,
  heapTotal: 28549545.984,
  heapUsed: 14863449.344,
  external: 4301431.0430000005,
  arrayBuffers: 57722.226
}
58.26920000000001 % Memory Usage {
  rss: 54357921.792,
  heapTotal: 28549545.984,
  heapUsed: 14879151.72,
  external: 4301431.0430000005,
  arrayBuffers: 57722.226
}
73.2424 % Memory Usage {
  rss: 54363668.480000004,
  heapTotal: 28549545.984,
  heapUsed: 14894674.512,
  external: 4301431.0430000005,
  arrayBuffers: 57722.226
}
```

图 8.12 手动部署应用内存使用情况。

图 8.13 中的结果表明，自动化系统大约将内存使用量降低了 1.3 倍，CPU 使用量降低了 1.7 倍。手动部署的应用具有更高的内存和 CPU 使用量。图 8.14 显示了使用未经过优化和资源供给的手动方法的结果快照。

已针对两个基于 AI 的应用（DownTube 和肥料推荐系统）对所提出的系统与手动部署进行了比较。表 8.1 展示了自动化系统与手动部署相比的性能。

```
4.3 % Memory Usage {
 rss: 28282880,
 heapTotal: 11198464,
 heapUsed: 7865616,
 external: 1341091,
 arrayBuffers: 60946
}

24.9 % Memory Usage {
 rss: 28352512,
 heapTotal: 11198464,
 heapUsed: 7883960,
 external: 1341131,
 arrayBuffers: 60946
}

30.3 % Memory Usage {
 rss: 28360794,
 heapTotal: 11198464,
 heapUsed: 7894992,
 external: 1341131,
 arrayBuffers: 60946
}

30.3 % Memory Usage {
 rss: 28385280,
 heapTotal: 11198464,
 heapUsed: 7905656,
 external: 1341131,
 arrayBuffers: 60946
}

31.2 % Memory Usage {
 rss: 28438528,
 heapTotal: 11198464,
 heapUsed: 7919776,
 external: 1341131,
 arrayBuffers: 60946
}
```

图 8.13 使用 PhasedJS 的自动化部署。

表 8.2 展示了手动部署和所提出系统的内存使用量和 CPU 使用量等指标。显示的结果表明，PhasedJS 中的 CPU 和内存使用量均较低。

PhasedJS 概述了 Web 自动化和部署如何帮助开发人员轻松管理和调试其 AI 应用。它能够根据用户应用的需求自动扩展目标应用并分配资源。这个革命性的框架还将帮助在同一台服务器上部署许多 AI 应用，同时保持最小的负载和更好的性能。日志和包通过 RSA1024 在空中加密，确保应用可共享数据的高度安全。在根级别，该框架旨在将基于 AI 的应用部署给所有不了解部署知识的用户，并使他们能够非常轻松地管理自己的应用，因为它将消除所有重复性任务，并帮助他们更好地专注于创新。

```
64.271999999999 % Memory Usage {
    rss: 32711565.312,
    heapTotal: 10291396.60000001,
    heapUsed: 8471902.896,
    external: 994331.286,
    arrayBuffers: 42110.1
}
52.884000000001 % Memory Usage {
    rss: 32727269.37600002,
    heapTotal: 10291396.60000001,
    heapUsed: 8486124.48,
    external: 994331.286,
    arrayBuffers: 42110.1
}
52.720800000001 % Memory Usage {
    rss: 32695861.748,
    heapTotal: 10291396.60000001,
    heapUsed: 8501777.424,
    external: 994331.286,
    arrayBuffers: 42110.1
}
53.04 % Memory Usage {
    rss: 32763912.192,
    heapTotal: 10291396.60000001,
    heapUsed: 8515999.008,
    external: 994331.286,
    arrayBuffers: 42110.1
}
53.04 % Memory Usage {
    rss: 32779610.25,
    heapTotal: 10291396.60000001,
    heapUsed: 8529903.048,
    external: 994331.286,
    arrayBuffers: 42110.1
}
53.04 % Memory Usage {
    rss: 32795320.32,
    heapTotal: 10291396.60000001,
    heapUsed: 8544115.008,
    external: 994331.286,
    arrayBuffers: 42110.1
}
```

图 8.14 未使用 PhasedJS 的手动部署。

- Amazon Web Services (AWS) (2023). https://aws.amazon.com/
- Babu, G. C. N., Gupta, S., Bhambri, P., Leo, L. M., Rao, B. H., & Kumar, S. (2021). A semantic health observation system development based on the IoT sensors. Turkish Journal of Physiotherapy and Rehabilitation, 32(3), 1721–1729.
- Benson, J. O., Prevost, J. J., & Rad, P. (2016, April). Survey of automated software deployment for computational and engineering research. In 2016 Annual IEEE Systems Conference (SysCon) (pp. 1–6). IEEE.
- Bhambri, P., Singh, M., Jain, A., Dhanoa, I. S., Sinha, V. K., & Lal, S. (2021). Classification of the gene expression data with the aid of optimized feature selection. Turkish Journal of Physiotherapy and Rehabilitation, 32(3), 1158–1167.
- Bose, M. M., Yadav, D., Bhambri, P., & Shankar, R. (2021). Electronic customer relationship management: Benefits and pre-implementation considerations. Journal of Maharaja Sayajirao University of Baroda, 55(01)(VI), 1343–1350.
- Canali, C., & Lancellotti, R. (2012, September). Automated clustering of VMs for scalable cloud monitoring and management. In SoftCOM 2012, 20th International Conference on Software, Telecommunications and Computer Networks (pp. 1–5). IEEE.
- Chen, H. S., Wu, C. H., Pan, Y. L., Yu, H. E., Chen, C. M., & Cheng, K. Y. (2013, December). Towards the automated fast deployment and clone of private cloud service: the Ezilla toolkit. In 2013 IEEE 5th International Conference on Cloud Computing Technology and Science (Vol. 1, pp. 136–141). IEEE.
- Danielsson, P., Postema, T., & Munir, H. (2021). Heroku-based innovative platform for web-based deployment in product development at axis. IEEE Access, 9, 10805–10819.
- Deshmukh, S. N., & Khandagale, H. P. (2017, April). A system for application deployment automation in a cloud environment. In 2017 Innovations in Power and Advanced Computing Technologies (i-PACT) (pp. 1–4). IEEE.
- Durairajan, S., & Sundararajan, P. (2013, October). Portable service management deployment over cloud platforms to support production workloads. In 2013 IEEE International Conference on Cloud Computing in Emerging Markets (CCEM) (pp. 1–7). IEEE.
- Giannakopoulos, I., Papailiou, N., Mantas, C., Konstantinou, I., Tsoumakos, D., & Koziris, N. (2014, October). Celar: Automated application elasticity platform. In 2014 IEEE International Conference on Big Data (Big Data) (pp. 23–25). IEEE.
- Huang, F., Li, H., Yuan, Z., & Li, X. (2017, May). An application deployment approach based on hybrid cloud. In 2017 IEEE 3rd International Conference on Big Data Security on Cloud (Big Data Security), IEEE International Conference on High Performance and Smart Computing (HPSC), and IEEE International Conference on Intelligent Data and Security (IDS) (pp. 74–79). IEEE.
- Jabeen, A., Pallathadka, H., Pallathadka, L. K., & Bhambri, P. (2021). E-CRM successful factors for business enterprises case studies. Journal of Maharaja Sayajirao University of Baroda, 55(01(VI)), 1332–1342.
- Juve, G., & Deelman, E. (2011, November). Automating application deployment in infrastructure clouds. In 2011 IEEE Third International Conference on Cloud Computing Technology and Science (pp. 658–665). IEEE.
- Karakostas, B. (2014, September). Towards autonomic cloud configuration and deployment environments. In 2014 International Conference on Cloud and Autonomic Computing (pp. 93–96). IEEE.
- Kikuchi, S. (2015, December). Prediction of workloads in incident management based on incident ticket updating history. In 2015 IEEE/ACM 8th International Conference on Utility and Cloud Computing (UCC) (pp. 333–340). IEEE.
- Kumar, P., Banerjee, K., Singhal, N., Kumar, A., Rani, S., Kumar, R., & Lavinia, C. A. (2022). Verifiable, secure mobile agent migration in healthcare systems using a polynomial-based threshold secret sharing scheme with a blowfish algorithm. Sensors, 22(22), 8620.
- Lu, H., Shtern, M., Simmons, B., Smit, M., & Litoiu, M. (2013, June). Pattern-based deployment service for next generation clouds. In 2013 IEEE Ninth World Congress on Services (pp. 464–471). IEEE.
- Microsoft Azure (2023). https://azure.microsoft.com/en-in/
- Ocone, L., Rak, M., & Villano, U. (2019, June). Benchmark-based cost analysis of auto scaling web applications in the cloud. In 2019 IEEE 28th International Conference on Enabling Technologies: Infrastructure for Collaborative Enterprises (WETICE) (pp. 98–103). IEEE.
- Quinton, C., Romero, D., & Duchien, L. (2014). Automated selection and configuration of cloud environments using software product lines principles. 2014 IEEE 7th International Conference on Cloud Computing (pp. 144–151). DOI: 10.1109/CLOUD.2014.29.
- Rachna, R., Chhabra, Y., & Bhambri, P. (2021). Various approaches and algorithms for monitoring energy efficiency of wireless sensor networks. In Harvinder Singh, Puneet Pal Singh Cheema, Prashant Garg (Eds.), Lecture Notes in Civil Engineering (Vol. 113, pp. 761–770). Springer, Singapore.

