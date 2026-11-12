
deployed, it is very difficult to see their run-time state, defined by their internal attributes. SmartInspect can pierce through the opaqueness and show to developers the live state of their own contracts while assuring a level of privacy that few other tools support. The inspector can see the contents of any contract instance of the given source code without needing to redeploy or develop any ad-hoc code to fetch the information. Contract inspection can help developers to better understand their contracts and even find bugs more easily.

Third, we presented Ukulele, a query language that allows users to retrieve information from the blockchain by writing SQL-like queries. This tool automates the task of sequentially searching into generic opaque structures and provides an easier way to specify the information we want to acquire in a higher abstraction level. Ukulele distinguishes itself by being able to search through all first-class elements such as blocks, transactions, accounts, and contracts. Other tools usually cannot search contract instances, leaving potential useful information behind. On the other hand, Ukulele is even able to call contract functions inside its queries.

For future work, we plan to extend the platform with more tools, such as: (1) improved metrics suite (our current SmartMetrics tools still needs improvement); (2) gas estimation of contract functions; (3) recommendation system to suggest secure programming practices; (4) a dashboard to facilitate the usage and interaction with blockchain and smart contracts.

## Bibliography

- [ABC+13] Vanessa Peña Araya, Alexandre Bergel, Damien Cassou, Stéphane Ducasse, and Jannik Laval. Agile Visualization With Roassal. In *Deep Into Pharo*, pages 209–239. Square Bracket Associates, September 2013.

- [ABC17] Nicola Atzei, Massimo Bartoletti, and Tiziana Cimoli. A Survey of Attacks on Ethereum Smart Contracts. In *Proceedings of International Conference on Principles of Security and Trust*, volume V 10204, pages 164–186. Springer, 2017.

- [ALSU06] Alfred V. Aho, Monica S. Lam, Ravi Sethi, and Jeffrey D. Ullman. *Compilers: Principles, Techniques, and Tools*, 2nd edition. Addison-Wesley Longman Publishing Co., Inc., Boston, MA, 2006.

- [BCDL13] Alexandre Bergel, Damien Cassou, Stéphane Ducasse, and Jannik Laval. Petitparser: Building Modular Parsers. In *Deep Into Pharo*, chapter 18, pages 377–411. Square Brackets Associates, 2013.

- [BDLF+16] Karthikeyan Bhargavan, Antoine Delignat-Lavaud, Cédric Fournet, Anitha Gollamudi, Georges Gonthier, Nadim Kobeissi, Natalia Kulatova, Aseem Rastogi, Thomas Sibut-Pinote, Nikhil Swamy, and Santiago Zanella-Béguelin. Formal Verification of Smart Contracts: Short Paper. In *2016 ACM Workshop on Programming Languages and Analysis for Security*, PLAS ’16, pages 91–96. ACM Press, New York, NY, 2016.

- [Ber16] Alexandre Bergel. *Agile Visualization*. LULU Press, 2016.

- [Bit18] Bitcoin.org. Bitcoin Developer Reference. *Bitcoin Core APIs*, 2018. Bitcoin Project 2009–2018.

- [BLGD17] John Brant, Jason Lecerf, Thierry Goubier, and Stéphane Ducasse. *Smaac, a Smalltalk Compiler-Compiler*, 2017. www.refactory.com/Software/SmaacCC/.

- [BLPB17] Massimo Bartoletti, Stefano Lande, Livio Pompianu, and Andrea Bracciali. A General Framework for Blockchain Analytics. In _1st Workshop on Scalable and Resilient Infrastructures for Distributed Ledgers_, SERIAL ’17, pages 7:1–7:6. ACM Press, New York, NY, USA, 2017.

- [BMB96] Lionel C. Briand, Sandro Morasca, and Victor Basili. Property-based Software Engineering Measurement. _Transactions on Software Engineering_, 22(1): 68–86, 1996.

- [BRDD18a] Santiago Bragagnolo, Henrique Rocha, Marcus Denker, and Stéphane Ducasse. Ethereum Query Language. In _1st International Workshop on Emerging Trends in Software Engineering for Blockchain (WETSEB)_, pages 1–8, May 2018.

- [BRDD18b] Santiago Bragagnolo, Henrique Rocha, Marcus Denker, and Stéphane Ducasse. SmartInspect: Solidity Smart Contract Inspector. In _2018 International Workshop on Blockchain Oriented Software Engineering (IWBOSE)_, pages 9–18, March 2018. Electronic ISBN: 978-1-5386-5986-1.

- [BRDD18c] Santiago Bragagnolo, Henrique Rocha, Marcus Denker, and Stéphane Ducasse. Ethereum Query Language. In _2018 IEEE/ACM 1st International Workshop on Emerging Trends in Software Engineering for Blockchain (WETSEB)_, pages 1–8, May 2018.

- [BU04] Gilad Bracha and David Ungar. Mirrors: Design Principles for Meta-level Facilities of Object-oriented Programming Languages. In _Proceedings of the International Conference on Object-Oriented Programming, Systems, Languages, and Applications (OOPSLA’04)_, _ACM SIGPLAN Notices_, pages 331–344. ACM Press, New York, NY, USA, 2004.

- [CCI90] Elliot Chikofsky and James Cross II. Reverse Engineering and Design Recovery: A Taxonomy. _IEEE Software_, 7(1): 13–17, January 1990.

- [CK94] Shyam R. Chidamber and Chris F. Kemerer. A Metrics Suite for Object Oriented Design. _IEEE Transactions on Software Engineering_, 20(6): 476–493, June 1994.

- [CLLZ17] Ting Chen, Xiaoqi Li, Xiapu Luo, and Xiaosong Zhang. Under-optimized Smart Contracts Devour Your Money. In _Proceedings of SANER_, pages 442–446. IEEE, 2017.

- [CNSG15] Andrei Chis, Oscar Nierstrasz, Aliaksei Syrel, and Tudor Girba. The Moldable Inspector. In _2015 ACM International Symposium on New Ideas, New Paradigms, and Reflections on Programming and Software (Onward!)_, _Onward!_, pages 44–60. ACM Press, New York, NY, USA, 2015.

- [DMO+18] Giuseppe Destefanis, Michele Marchesi, Marco Ortu, Roberto Tonelli, Andrea Bracciali, and Robert M. Hierons. Smart Contracts Vulnerabilities: A Call for Blockchain Software Engineering? In _2018 International Workshop on Blockchain Oriented Software Engineering, IWBOSE@SANER 2018, Campobasso, Italy, March 20, 2018_, pages 19–25, 2018.

- [EN10] Ramez Elmasri and Shamkant Navathe. _Fundamentals of Database Systems_, 6th edition. Addison-Wesley Publishing Company, USA, 2010.

- [Eth14] Ethereum Foundation. Ethereum’s White Paper, 2014.

- [Eth16] Ethereum Community. Ethereum Homestead Documentation, 2016.

- [Eth18a] Ethereum Foundation. Json RPC, 2018.

- [Eth18b] Ethereum Foundation. Remix Documentation Release 1, 2018. https://remix.readthedocs.io/en/latest.

- [Eth18c] Ethereum Foundation. Solidity Documentation Release 0.4.24, 2018.

- [Few06] S. Few. _Information Dashboard Design_. O’Reilly, 2006.

- [Hev97] A. R. Hevner. Phase Containment Metrics for Software Quality Improvement. _Information and Software Technology_, 39(13): 867–877, 1997.

- [HM95] M. Hitz and B. Montazeri. Measure Coupling and Cohesion in Object-oriented Systems. _Proceedings of International Symposium on Applied Corporate Computing (ISAAC ’95)_, October 1995.

- [IM15] Chinawat Isradisaikul and Andrew C. Myers. Finding Counterexamples From Parsing Conflicts. In 36th ACM SIGPLAN Conference on Programming Language Design and Implementation, PLDI '15, pages 555–564. ACM Press, New York, NY, 2015.

- [KGC+17] H. Kalodner, S. Goldfeder, A. Chator, M. Möser, and A. Narayanan. BlockSci: Design and Applications of a Blockchain Analysis Platform. ArXiv e-prints, September 2017.

- [LBGD18] Jason Lecerf, John Brant, Thierry Goubier, and Stéphane Ducasse. A Reflexive and Automated Approach to Syntactic Pattern Matching in Code Transformations. In IEEE International Conference on Software Maintenance and Evolution (ICSME'18), Madrid, Spain, September 2018.

- [LCO+16] Loi Luu, Duc-Hiep Chiu, Hrishikesh Olickel, Prateek Saxena, and Aquinas Hobor. Making Smart Contracts Smarter. In CCS'2016 (ACM Conference on Computer and Communications Security), 2016.

- [LH93] W. Li and S. Henry. Object Oriented Metrics that Predict Maintainability. Journal of Software Systems, 23(2): 111–122, 1993.

- [LK94] Mark Lorenz and Jeff Kidd. Object-Oriented Software Metrics: A Practical Guide. Prentice-Hall, 1994.

- [LKG07] Adrian Lienhard, Adrian Kuhn, and Orla Greevy. Rapid Prototyping of Visualizations Using Mondrian. In Proceedings IEEE International Workshop on Visualizing Software for Understanding, Vissof'07, pages 67–70. IEEE Computer Society, Los Alamitos, CA, June 2007.

- [Mer93] Gary Merrill. Parsing Non-LR(k) Grammars With Yacc. Software Practice and Experience, 2(8): 829–850, 1993.

- [Mil05] Ashley Mills. Antlr Tutorial, 2005.

- [MM18] S. Morishima and H. Matsutani. Accelerating Blockchain Search of Full Nodes Using Gpus. In 26th Euromicro International Conference on Parallel, Distributed and Network-based Processing (PDP), pages 244–248, March 2018.

- [NA05] Oscar Nierstrasz and Franz Achermann. Separating Concerns With First-class Namespaces. In Robert E. Filman, Tzilla Elrad, Siobhán Clarke, and Mehmet Aksit, editors, Aspect-Oriented Software Development, pages 243–259. Addison-Wesley, 2005.

- [PBB07] Leonardo Teixeira Passos, Mariza A. S. Bigonha, and Roberto S. Bigonha. A Methodology for Removing LALR(k) Conflicts. Journal of Universal Computer Science, 13(6): 737–752, June 2007.

- [PBD+15] Nick Papoulias, N. Bouraqadi, Marcus Denker, Stéphane Ducasse, and Luc Fabresse. Mercury: Properties and Design of a Remote Debugging Solution Using Reflection. Journal of Object Technology, 2015.

- [PPMT17] S. Porru, A. Pinna, M. Marchesi, and R. Tonelli. Blockchain-oriented Software Engineering: Challenges and New Directions. In Proceedings of the 39th International Conference on Software Engineering Companion, pages 169–171, 2017.

- [RDDL17] Henrique Rocha, Stéphane Ducasse, Marcus Denker, and Jason Lecerf. Solidity Parsing Using Smacc: Challenges and Irregularities. In Proceedings of the 12th Edition of the International Workshop on Smalltalk Technologies, IWST '17, pages 2:1–2:9. ACM Press, New York, NY, 2017.

- [RSI+17] Michele Ruta, Floriano Scioscia, Saverio Ieva, Giovanna Capurso, and Eugenio Di Sciascio. Supply Chain Object Discovery With Semantic-enhanced Blockchain. In Proceedings of the 15th ACM Conference on Embedded Network Sensor Systems, SenSys '17, pages 60:1–60:2. ACM Press, New York, NY, 2017.

- [SKS11] Abraham Silberschatz, Henry Korth, and S. Sudarshan. Database Systems Concepts, 6th edition. McGraw-Hill, Inc., New York, NY, 2011.
