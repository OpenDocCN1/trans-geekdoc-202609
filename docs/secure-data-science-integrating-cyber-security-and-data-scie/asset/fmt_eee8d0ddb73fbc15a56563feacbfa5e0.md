
In this chapter, we have proposed an extensible fine-grained online social network access control model based on semantic web tools. In addition, we propose authorization, admin and filtering policies that are modeled using `OWL` and `SWRL`. The architecture of a framework in support of this model has also been presented. We also described the implementation of an extensible fine-grained online social network access control model based on semantic web tools. In particular we discussed the implementation of the authorization, administration, and filtering policies that are modeled using `OWL` and `SWRL`. That is, we discussed the implementation of a version of the framework described in [Chapter 19](#ch19.xhtml#chapter19) and presented experimental results for the length of time access control can be evaluated using this scheme. Further work could be conducted in the area of determining a minimal set of access policies that could be used in evaluating access requests in a further attempt to increase the efficiency of these requests.

We intend to extend this work toward several directions. A first direction arises by the fact that supporting flexible admin policies could bring the system to a scenario where several access control policies specified by distinct users can be applied to the same resource. Indeed, in our framework social network's resources could be related to different users according to the supported ontology. For example, a given photo could be connected to the owner, say Bob, as well as to all users with which is tagged with, say Alice and Carl. According to the semantics of admin policies, it could be the case that some of these tagged users are authorized to specify access control policies for that resource, say only Alice. For example, Alice could have specified that the photos tagged to her can be accessed only by her direct friends, whereas Bob could have specified that his photos have to be accessed by his direct friend and colleagues. To enforce access control, the framework has to decide how the specified access control policies have to be combined together. As such, a first important extension of the proposed framework will be the support of a variety of policy integration strategies. As a further important future work, we plan to implement our framework using the ideas discussed in this chapter and test the efficiency of various ways of combining forward- and backward-chaining based reasoning for different scenarios.

Additionally, we have shown that existing social networks need some form of reasonable data partitioning in order for semantic inference of their access control to be reasonable in its speed and memory requirements, due to constraints on the memory available to perform inference. Additionally, further work can be used in determining the best method of representing the individual information of a person in a social network to determine whether a hybrid semantic/relational approach or a pure approach offers the best overall system.

## References

*   `[ALI2007]` [B. Ali](#ch17.xhtml#Cref17_1), W. Villegas, M. Maheswaran, A Trust Based Approach for Protecting User Data in Social Networks, *2007 Conference of the Center for Advanced Studies on Collaborative research (CASCON’07)*, 2007, pp. 288–293.

*   `[BERT2007]` [S. Berteau](#ch17.xhtml#Cref17_2), Facebook's misrepresentation of Beacon's Threat to Privacy: Tracking Users Who Opt Out or Are Not Logged. CA Security Advisor Research Blog, March 2007. Available at: [http://community.ca.com/blogs/securityadvisor/archive/2007/11/29/facebook-s-misrepresentation-of-beacon-s-threat-to-privacy-tracking-users-who-opt-out-or-are-not-logged-in.aspx](http://community.ca.com).

*   `[BRIC2007]` [D. Brickley](#ch17.xhtml#Cref17_3), L. Miller, FOAF Vocabulary Specification 0.91, RDF Vocabulary Specification, November 2007. Available at [http://xmlns.com/foaf/0.1](http://xmlns.com).

*   `[CARM2008]` [B. Carminati](#ch17.xhtml#Cref17_4), E. Ferrari, A. Perego, Security and Privacy in Social Networks, volume VII of Encyclopedia of Information Science and Technology, IGI Publishing, 2nd edition, 2008, pp. 3369–3376.

*   `[CARM2009a]` B. Carminati, E. Ferrari, R. Heatherly, M. Kantarcioglu, B.M. Thuraisingham, A Semantic Web Based Framework for Social Network Access Control, In B. Carminati and J. Joshi, editors, SACMAT, ACM, 2009, pp. 177–186.

*   `[CARM2009b]` B. Carminati, E. Ferrari, A. Perego, Enforcing Access Control in Web-based Social Networks, ACM Transactions on Information Systems Security, Volume 13, # 1, 2009, pp. 1–38.

*   `[CHOI2006]` H. Choi, S. R. Kruk, S. Grzonkowski, K. Stankiewicz, B. Davis, J. G. Breslin, Trust Models for Community Aware Identity Management, The Identity, Reference and Web Workshop (IRW2006) at the 15th International World Wide Web Conference (WWW2006), 2006.

*   `[CARM2011]` [B. Carminati](#ch17.xhtml#Cref17_8), E. Ferrari, R. Heatherly, M. Kantarcioglu, B. Thuraisingham, Semantic Web-based Social Network Access Control, Computers & Security, Volume 30, #2-3, 2011, pp. 108–115.

*   `[ELAH2008]` [N. Elahi](#ch17.xhtml#Cref17_9), M.M.R. Chowdhury, J. Noll, Semantic Access Control in Web Based Communities, *Computing in the Global Information Technology, 2008. ICCGI’08. The Third International Multi-Conference, Washington, DC, USA*, 2008, pp. 131–136.

*   `[FINI2008]` [T. W. Finin](#ch17.xhtml#Cref17_10), A. Joshi, L. Kagal, J. Niu, R.S. Sandhu, W.H. Winsborough, B.M. Thuraisingham, R. OWL BAC: Representing Role based Access Control in OWL, In I. Ray and N. Li, editors, SACMAT, ACM, 2008, pp. 73–82.

*   `[HORR2004]` [I. Horrocks](#ch17.xhtml#Cref17_11), P.F. Patel-Schneider, H. Boley, S. Tabet, B. Grosof, M. Dean, SWRL: A Semantic Web Rule Language Combining OWL and RuleML. W3C Member Submission, World Wide Web Consortium, May 2004. Available at: [http://www.w3.org/Submission/SWRL](http://www.w3.org).

*   `[KRUK2006]` [S.R. Kruk](#ch17.xhtml#Cref17_12), S. Grzonkowski, A. Gzella, T. Woroniecki, H. Choi, D-FOAF: Distributed Identity Management with Access Rights Delegation, In R. Mizoguchi, Z. Shi, and F. Giunchiglia, editors, ASWC, volume 4185 of Lecture Notes in Computer Science, Springer, 2006, pp. 140–154.

*   `[MIKA2007]` [P. Mika](#ch17.xhtml#Cref17_13), Social Networks and the Semantic Web, Springer, 2007.

*   `[THUR2020]` [B. Thuraisingham](#ch17.xhtml#Cref17_14), Multigenerational Database Inference Controllers, *IEEE Big Data Security Conference*, May 2020.

*   `[TONT2003]` [G. Tonti](#ch17.xhtml#Cref17_15), J.M. Bradshaw, R. Jeffers, R. Montanari, N. Suri, A. Uszok, Semantic Web Languages for Policy Representation and Reasoning: A Comparison of KAoS, rei, and ponder, In D. Fensel, K.P. Sycara, and J. Mylopoulos, editors, International Semantic Web Conference, volume 2870 of Lecture Notes in Computer Science, Springer, 2003, pp. 419–437.

*   `[WWW2006]` [World Wide Web Consortium](#ch17.xhtml#Cref17_16), Defining n-ary Relations on the Semantic Web, 2006, [http://www.w3.org/TR/swbp-n-aryRelations/](http://www.w3.org)

*   `[WWW1999]` [World Wide Web Consortium](#ch17.xhtml#Cref17_17), Status for Resource Description Framework (rdf) Model and Syntax Specification, 1999, [http://www.w3.org/1999/.status/PR-rdf-syntax-19990105/status](http://www.w3.org)

*   `[YAGU2005]` [M.L. Yague](#ch17.xhtml#Cref17_18), M.-del-M. Gallardo, A. Mana, Semantic Access Control Model: A Formal Specification, ESORICS: European Symposium on Research in Computer Security, LNCS, Springer-Verlag, 2005.

# 18 Inference and Access Control for Big Data

DOI: [10.1201/9781003081845-29](https://doi.org/10.1201/9781003081845-29)

## 18.1 Introduction
