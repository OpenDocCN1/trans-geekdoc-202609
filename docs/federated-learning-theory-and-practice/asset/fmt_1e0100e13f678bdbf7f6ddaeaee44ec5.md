
*   [28] Brendan McMahan, Eider Moore, Daniel Ramage, Seth Hampson, Blaise Aguera y Arcas, Communication-efficient learning of deep networks from decentralized data, *Proceedings of the International Conference on Artificial Intelligence and Statistics*. April 2017.

*   [29] Mehryar Mohri, Gary Sivek, Ananda Theertha Suresh, Agnostic federated learning, [arXiv:1902.00146](http://www.arxiv.org/abs/1902.00146); Jan. 2019.

*   [30] Alex Nichol, Joshua Achiam, John Schulman, On first-order meta-learning algorithms, [arXiv:1803.02999](http://www.arxiv.org/abs/1803.02999); Oct. 2018.

*   [31] Krishna Pillutla, Sham M. Kakade, Zaid Harchaoui, Robust aggregation for federated learning, [arXiv:1912.13445](http://www.arxiv.org/abs/1912.13445); Dec. 2019.

*   [32] L.Y. Pratt, Discriminability-based transfer between neural networks, S. Hanson, J. Cowan, C. Giles, eds. *Advances in Neural Information Processing Systems*. 1992;vol. 5:204–211.

*   [33] Sashank Reddi, Zachary Charles, Manzil Zaheer, Zachary Garrett, Keith Rush, Jakub Konečný, Sanjiv Kumar, H. Brendan McMahan, Adaptive federated optimization, [arXiv:2003.00295](http://www.arxiv.org/abs/2003.00295); Feb. 2020.

*   [34] Felix Sattler, Klaus-Robert Müller, Wojciech Samek, Clustered federated learning: model-agnostic distributed multitask optimization under privacy constraints, *IEEE Transactions on Neural Networks and Learning Systems* 2021;32(8):3710–3722.

*   [35] Virginia Smith, Chao-Kai Chiang, Maziar Sanjabi, Ameet Talwalkar, Federated multi-task learning, *Proceedings of the International Conference on Neural Information Processing Systems*. 2017.

*   [36] Baochen Sun, Jiashi Feng, Kate Saenko, Return of frustratingly easy domain adaptation, *Proceedings of the Thirtieth AAAI Conference on Artificial Intelligence*. 2016:2058–2065.

*   [37] Alysa Ziying Tan, Han Yu, Lizhen Cui, Qiang Yang, Towards personalized federated learning, *IEEE Transactions on Neural Networks and Learning Systems* 2022:1–17.

*   [38] Kangkang Wang, Rajiv Mathews, Chloé Kiddon, Hubert Eichner, Franccoise Beaufays, Daniel Ramage, Federated evaluation of on-device personalization, [arXiv:1910.10252](http://www.arxiv.org/abs/1910.10252); 2019.

*   [39] Tao Yu, Eugene Bagdasaryan, Vitaly Shmatikov, Salvaging federated learning by local adaptation, [arXiv:2002.04758](http://www.arxiv.org/abs/2002.04758); 2020.

---

# Chapter 8: Fairness in federated learning

Xiaoqiang Lin^[a](#Chp008_143-160_B9780443190377000168.xhtml#aff0010); Xinyi Xu^[a](#Chp008_143-160_B9780443190377000168.xhtml#aff0010); Zhaoxuan Wu^[a](#Chp008_143-160_B9780443190377000168.xhtml#aff0010); Rachael Hwee Ling Sim^[a](#Chp008_143-160_B9780443190377000168.xhtml#aff0010); See-Kiong Ng^[a](#Chp008_143-160_B9780443190377000168.xhtml#aff0010); Chuan-Sheng Foo^[a](#Chp008_143-160_B9780443190377000168.xhtml#aff0010); Patrick Jaillet^[b](#Chp008_143-160_B9780443190377000168.xhtml#aff0015); Trong Nghia Hoang^[c](#Chp008_143-160_B9780443190377000168.xhtml#aff0020); Bryan Kian Hsiang Low^[a](#Chp008_143-160_B9780443190377000168.xhtml#aff0010)

^a National University of Singapore, Singapore, Singapore

^b Massachusetts Institute of Technology, Cambridge, MA, United States

^c Washington State University, Pullman, WA, United States

## Abstract

Federated learning (FL) enables a form of collaboration among multiple clients in jointly learning a machine learning (ML) model without centralizing their local datasets. Like in any collaboration, it is imperative to guarantee *fairness* so that the clients are willing to participate. For instance, it is unfair if one client benefits significantly more than others, or if some client benefits disproportionately to its contribution in the collaboration. Additionally, it is also unfair if the ML model makes biased predictions against certain groups of clients. This chapter discusses three specific notions of fairness by highlighting their motivations from real-world use-cases, examining several specific definitions for each notion and lastly describing the corresponding algorithms proposed to achieve each notion of fairness. At the end, this chapter will also summarize the identified gaps in current research efforts into open problems.

### Keywords

Fairness; Federated learning

## Acknowledgements

This research/project is supported by the National Research Foundation Singapore and DSO National Laboratories under the AI Singapore Programme (AISG Award No: AISG2-RP-2020-018).

## 8.1 Introduction

Federated learning (FL) [[15]](#Chp008_143-160_B9780443190377000168.xhtml#br0075) allows multiple clients to collaborate in training a model with better performance (than before collaboration) without centralizing their local datasets [[5](#Chp008_143-160_B9780443190377000168.xhtml#br0025),[30]](#Chp008_143-160_B9780443190377000168.xhtml#br0150). However, most existing FL systems [[5](#Chp008_143-160_B9780443190377000168.xhtml#br0025),[15](#Chp008_143-160_B9780443190377000168.xhtml#br0075),[27](#Chp008_143-160_B9780443190377000168.xhtml#br0135),[30](#Chp008_143-160_B9780443190377000168.xhtml#br0150),[31]](#Chp008_143-160_B9780443190377000168.xhtml#br0155) do not explicitly consider the willingness and simply assume that all clients want to collaborate [[15]](#Chp008_143-160_B9780443190377000168.xhtml#br0075). This assumption can be problematic when the clients are self-interested and not obliged to participate. For example, clients might not participate if they are treated *unfairly* (e.g., receiving no or less reward while contributing resources) by the FL system. Therefore, it is imperative to guarantee *fairness* to encourage such collaborations in FL. This chapter discusses three fairness notions, *equitable fairness*, *collaborative fairness* and *algorithmic fairness*, by (1) motivating them in Section [8.1](#Chp008_143-160_B9780443190377000168.xhtml#s0010); (2) providing the formal definitions in Section [8.2](#Chp008_143-160_B9780443190377000168.xhtml#s0015); (3) describing the respective algorithms for achieving them in Section [8.3](#Chp008_143-160_B9780443190377000168.xhtml#s0035); and (4) shedding light on some open problems in Section [8.4](#Chp008_143-160_B9780443190377000168.xhtml#s0055).

FL systems can be viewed as a form of cost-sharing or resource-allocation collaboration. The clients share the costs of collecting data by tapping into the information from others' local datasets to train a `global model` (i.e., model trained on the server). The global model can be viewed as a "medium" of some resources to be allocated to the clients. Each client receives the same global model to make predictions on their local datasets.
