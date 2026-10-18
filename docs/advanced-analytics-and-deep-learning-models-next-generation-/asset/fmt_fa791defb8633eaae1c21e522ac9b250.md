
33\. Mallik, S. and Sahoo, A.K., A Comparison Study of Different Privacy Preserving Techniques in Collaborative Filtering Based Recommender System, in: *Computational Intelligence in Data Mining*, pp. 193–203, Springer, Singapore, 2020.

34\. Sahoo, A.K. and Pradhan, C., Accuracy-Assured Privacy-Preserving Recommender System Using Hybrid-Based Deep Learning Method, in: *Recommender System with Machine Learning and Artificial Intelligence: Practical Tools and Applications in Medical, Agricultural and Other Industries*, pp. 101–120, 2020.

1. [\*](#c03.xhtml#aut1)*Corresponding author*: [abhayakumarsahoo2012@gmail.com](mailto:abhayakumarsahoo2012@gmail.com)

# 4 Adoption of Machine/Deep Learning in Cloud With a Case Study on Discernment of Cervical Cancer

**Jyothi A. P. ^([1](#c04.xhtml#aff1),[2](#c04.xhtml#aff2))[\*](#c04.xhtml#raut1), S. Usha^([2](#c04.xhtml#aff2),[3](#c04.xhtml#aff3)) and Archana H. R.^([3](#c04.xhtml#aff3))**

*^([1](#c04.xhtml#raff1))Dept. of CSE, RVITM, Bengaluru, Karnataka, India*

*^([2](#c04.xhtml#raff2))Dept. of CSE, RND, RRCE, Bengaluru Karnataka, India*

*^([3](#c04.xhtml#raff3))Dept. of ECE, BMSCE, Bengaluru, Karnataka, India*

> **Abstract**

> Machine learning (ML) utilizes calculations to parse information and settle on educated choices dependent on what it has realized. Deep learning (DL) is a subfield of ML. While both fall under the general classification of artificial intelligence, profound realizing is the thing that controls the most human-like man-made consciousness.

> The association between ML/DL and cloud computing is the interest for resources. Where cloud computing becomes possibly the most important factor is the quick capacity to turn up new servers with a pre-characterized picture and change assets on the fly. You may need 100 servers up chipping away at your calculation, yet you do not need those hundred servers up consistently, which would be a misuse of cash. With cloud computing, you can turn up any number of servers you need, work on the algorithm, and, at that point, destroy the machines again when complete.

> This book chapter discusses on adoption of ML/DL in cloud. It covers introduction, background study, description of ML/DL, connection between ML/DL and cloud, ML/DL algorithms, a project implementation on discernment of cervical cancer by using ML/DL in cloud with its design methodology and results, applications like cognitive cloud, chatbots, and smart personal assistants, IoT cloud, business intelligence, AI-as-a-Service, etc., along with advantages and conclusion related to adoption of ML/DL in cloud.

> Definite and blunder-free location can spare lives. Prior identification of cervical disease was finished by a tiny smear test dependent on the figuring of boundaries of the phone core of the example, for example, its shape and size as smear is broke down to magnifying lens is an incredibly testing task. Thus, Digital Image Processing procedure is required to distinguish anomalies in human cell. Subsequently, a thorough AI procedure has been proposed in this book section. The proposed method gives the highlights and state of cytoplasm, nucleus in the cervix cell. KNN and SVM are used with the highlights and state of the divided cell and contrasted and obscure cervix cell test with this procedure. The precision pace of 86% for SVM and 70% for KNN is accomplished.

> While ML/DL makes cloud computing much more enhanced, efficient, and scalable, the cloud platform expands the horizon for ML/DL applications. Thus, both are intricately interrelated, and when combined into a symbiotic relationship, the business connotations can be tremendous.

> **Keywords:** Machine learning, deep learning, KNN, SVM, cloud, AI, cervical cancer

## 4.1 Introduction

Artificial Intelligence (AI) utilizes calculation to parse data, gains from that information, and settles on educated choices dependent on what it has realized. Machine Learning (ML)/Deep Learning (DL) are a subdomain AI. Both come under the broad category of artificial brainpower, thoughtful realizing is the obsession that reins the most human being-like artificial consciousness.

Both of these subsets of AI are some manner or another linked with data, which makes it plausible to articulate to an explicit type of understanding. On the other hand, you should know that profound knowledge require substantially more data than a conventional AI computation. The purpose in the wake of this is that profound knowledge organizations can recognize a variety of mechanism in neural organization layers presently when in excess of 1,000,000 information focuses communicate. AI calculations, then again, are equipped for learning by pre-modified models.

Distributed computing is the on-request ease of access of personal computer framework resources, predominantly data stockpile and power. It portrays server farms available to several patrons over the Internet.

The association between ML/DL and cloud processing is the interest for assets. ML/DL is a cycle that requires a ton of preparing power. Numerous individuals keen on this will consolidate many workers without a moment’s delay to chip away at a calculation, and request power that is not effectively available on dedicated facilitating stages, and so on. The advancement of artificial intelligence and the evolution with deep learning and machine learning is signified in [Figure 4.1](#c04.xhtml#fig4-1).

![Figure 4.1 Advancement of artificial intelligence.](images/fig4-1.jpg)

[**Figure 4.1**](#c04.xhtml#rfig4-1) Advancement of artificial intelligence.

Where distributed computing becomes possibly the most important factor is the fast capacity to turn up new workers with a pre-characterized picture, and change assets on the fly. You may need 100 workers up chipping away at your calculation; however, you do not need those hundred workers up consistently in any case, which would be a misuse of cash.

With distributed computing, you can turn up quite a few workers you need, chip away at the calculation, and, at that point, obliterate the machines again when complete.

As more cloud administration suppliers and organizations understand the capability of ML/DL in the cloud, it will prod the interest for cloud ML/DL stages. Although ML/DL makes distributed computing substantially more upgraded, effective, and versatile, the cloud stage grows the skyline for ML/DL applications. Hence, both are complicatedly interconnected. When consolidated, the business undertones might be gigantic. The interrelativity of AI, ML and DL is represented in [Figure 4.2](#c04.xhtml#fig4-2).

Preparing ML models in the cloud bodes well. Why? Among numerous reasons, it permits you to prepare on a lot of information with ample figure and maybe train numerous models in equal. Additionally it is not difficult to do! On Google Cloud Platform, you can utilize Cloud ML Engine to prepare AI models in Tensor Flow and other Python ML libraries (for example, scikit-learn) without dealing with any foundation. To do this, you should place your code into a Python bundle (for example, add setup.py and \_\_init\_\_.py records). Likewise, it is a best practice to put together your code into a model.py and task.py.

![Figure 4.2 AI, ML, and DL.](images/fig4-2.jpg)

[**Figure 4.2**](#c04.xhtml#rfig4-2) AI, ML, and DL.

Man-made reasoning as a scholastic order was established in 1950s. As a matter of fact, the “man-made intelligence” phrase was instituted by John McCarthy, an American PC researcher. As indicated by John McCarthy, AI is “The discipline and designing and construction of canny machinery, particularly clever PC programs”.
