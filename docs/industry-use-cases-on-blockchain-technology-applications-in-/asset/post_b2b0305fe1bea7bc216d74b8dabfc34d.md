
Shehhi, A. A., Oudah, M., & Aung, Z. (2014). Investigating factors behind choosing a cryptocurrency. 2014 IEEE International Conference on Industrial Engineering and Engineering Management, 1443–1447. 10.1109/IEEM.2014.7058877

Shrestha, B., Halgamuge, M. N., & Treiblmaier, H. (2020). Using Blockchain for Online Multimedia Management: Characteristics of Existing Platforms. In Blockchain and Distributed Ledger Technology Use Cases (pp. 289–303). Springer.

Tama, B. A., Kweka, B. J., Park, Y., & Rhee, K.-H. (2017). A critical review of blockchain and its current applications. 2017 International Conference on Electrical Engineering and Computer Science (ICECOS), 109–113. 10.1109/ICECOS.2017.8167115

Toyoda, K., Ohtsuki, T., & Mathiopoulos, P. T. (2017). Identification of High Yielding Investment Programs in Bitcoin via Transactions Pattern Analysis. GLOBECOM 2017 - 2017 IEEE Global Communications Conference, 1–6. 10.1109/GLOCOM.2017.8254420

Tschorsch, F., & Scheuermann, B. (2016). Bitcoin. IEEE Communications Surveys and Tutorials, 18(3), 2084–2123. doi:10.1109/COMST.2016.2535718

Upadhyaya, R., & Jain, A. (2016). Cyber ethics and cybercrime: A deep dwelled study into legality, ransomware, underground web and bitcoin wallet. 2016 International Conference on Computing, Communication and Automation (ICCCA), 143–148. 10.1109/CCAA.2016.7813706

Van Der Horst, L., Choo, K.-K. R., & Le-Khac, N.-A. (2017). Process Memory Investigation of the Bitcoin. IEEE Access: Practical Innovations, Open Solutions, 5, 22385–22398. doi:10.1109/ACCESS.2017.2759766

Wang, Q., Li, X., & Yu, Y. (2018). Anonymity. IEEE Access: Practical Innovations, Open Solutions, 6, 12336–12341. doi:10.1109/ACCESS.2017.2787563

Wang, Y., & Gao, J. (2018). A Regulation Scheme Based on the Ciphertext-Policy Hierarchical Attribute-Based Encryption in Bitcoin. IEEE Access: Practical Innovations, Open Solutions, 6, 16267–16278. doi:10.1109/ACCESS.2018.2814620

Yin, W., Wen, Q., Li, W., Zhang, H., & Jin, Z. (2018). An Anti-Quantum Transaction Authentication Approach in Blockchain. IEEE Access: Practical Innovations, Open Solutions, 6, 5393–5401. doi:10.1109/ACCESS.2017.2788411

Zhang, Y., & Li, J. (2016, June 30). An Automatic Identification Authentic Work Anti-counterfeiting Algorithm Based on DWT-DCT. International Journal of Security and Its Applications, 10(6), 135–144. doi:10.14257/ijsia.2016.10.6.14

## Chapter 8

## A Securities Settlement Model Using Blockchain Technology for Central Securities Depository

Andre P. Calitz
Nelson Mandela University, South Africa

Jean H. Greyling
https://orcid.org/0000-0002-6773-9200
Nelson Mandela University, South Africa

Steve Everett
Nelson Mandela University, South Africa

### ABSTRACT

Post-trade securities settlements entered the electronic age between 1980 and 2000. The introduction of technologies such as secure electronic messaging, and improvements in database technology, enabled the inception of central securities depositories (CSDs) as trusted third parties or intermediaries within the securities settlements post-trade landscape. The study reported in this chapter has a focus on CSDs and the application of the blockchain technology to securities settlements. The objective is to develop a model for securities settlements using blockchain technology for a CSD, as currently, globally, no CSD has introduced a production-ready blockchain-based solution for securities settlements. A conceptual model was created from the reported literature that was evaluated by international post-trade securities professionals. The findings have resulted in the acceptance of the main components of the model, with a focus on the cost of the solution, and with the identification of prerequisites to such a solution (e.g., legal/regulatory enablement).

### INTRODUCTION

The financial services industry has introduced new payment methods and services globally as new technologies have emerged. The use of mobile devices and banking applications (Apps) have made banking services more accessible that have improved the user experience. Electronic cash can now be sent on a peer-to-peer basis (transfer of value) without the need for a financial services intermediary (Nakamoto, 2008). Both the cash and stocks (e.g. securities traded on a financial exchange) have value and can be transferred typically between a buyer and a seller. A buyer of stock interacts directly with a seller of that stock or the issuer of stock (e.g. a company which issues either an equity or debt stock), having the ability in the network to view the transaction (Gibson and Kirk, 2016).

Cryptocurrencies, such as Bitcoin, Litecoin and Ethereum, have introduced a digital asset that can be exchanged between two parties. Peer-to-peer transactions are the core type of transaction which are undertaken in the Bitcoin Blockchain, that makes use of a cryptocurrency known as Bitcoin, which uses cryptography to secure peer-to-peer transactions in a verifiable database that cannot be changed or amended without detection (Swanson, 2015). Typically, these transactions can take place without geographical restriction and without the need to use the traditional banking services to do so.

Securities settlement is a business process whereby securities are delivered against a cash payment between two parties. The opportunity to achieve this type of peer-to-peer transaction in securities settlements (whereby an equity or debt instrument for example can be exchanged for cash) has resulted in much hype within the financial services sector, as the potential for disintermediation of financial services intermediaries exists within the securities settlements ecosystem (Gartner, 2020).

Gartner (2020) indicates that Blockchain technology is at the peak of inflated expectations. It is important to note that, although the technology in its current form is relatively new, many of the cryptographic techniques employed were developed as early as the 1970s (KPMG, 2018). Therefore, since the technology is underpinned by well-known cryptographic techniques and has been applied in the Bitcoin ecosystem, its application in securities settlements needs to be further explored.

Over the last two decades, the traditional trading floors at stock exchanges have been replaced by virtual trading floors, however, whether virtual or physical, each provided the ability to connect investors wishing to buy and sell stocks (O’Connor, 2004). The processes, thereafter, allow the exchange of cash and securities after the trade in what is commonly known as the ‘post-trade’ process. The process has not undergone a significant change in the last 10 to 15 years despite various technological advances in Financial Services over this period.

In the trade to the post-trade environments, there are multiple, trusted third parties, such as Exchanges, Brokers, Dealers and Central Securities Depositories (CSDs). Karp (2015) highlights the potential to disrupt this particular sector of Financial Services through the use of Blockchain. CSDs, for example, are typically a trusted third party in most markets, which may only have one, or a small number of CSDs responsible for securities settlements in a specific market.

Blockchain technology creates new opportunities and has great potential for securities settlements as a platform. The ability to exchange assets on a peer-to-peer basis, confirmed by an algorithm, is an appealing prospect to improve efficiency and reduce costs in any market. The technology, however, is not new and has been widely developed and documented for more than a decade.

This chapter aims to investigate why blockchain technology has not been successfully translated into a blockchain based production system for securities settlements. A model for securities settlements has been proposed using Blockchain technology. The model has been evaluated by a team of international role players.

### PROBLEM STATEMENT AND RESEARCH OBJECTIVE

At the time of publication of this research study, no Central Securities Depository (CSD) exists that is settling securities using Blockchain technology globally, although many had issued press releases on planned research and implementations. In addition, the cryptocurrency market has continued to grow in parallel to the existing securities market. Therefore, the research problem investigated in this study is as follows:

No Central Securities Depository (CSD), nor any Capital Markets infrastructure presently utilise the Blockchain technology for securities settlements.

The current research was initiated by identifying what risks a CSD mitigates, given the actors, intermediaries and various settlement models employed; and how existing technology and processes assist in achieving a successful outcome. Once these were identified, the research explored what expectations of securities settlements exist amongst the primary role players in capital markets securities settlements (namely the regulators, issuers and investors). The research evaluated the most suitable approach to implement the new blockchain technology in an established securities settlement market. This provided a balanced evaluation, consisting of the inherent risks and the perceived benefits of available Blockchain technologies. A conceptual model was then presented and its acceptance evaluated, not only by CSDs, but also by the primary international role players in the industry.

The main research question for the study is:

What are the perceptions of the international role players in the industry, for a proposed model for securities settlements using Blockchain technology?

The main research objective of the study is:

To evaluate a proposed model for securities settlements using Blockchain technology for a Central Securities Depository by international role players.

This study is focused on CSDs and the application of the Blockchain technology to securities settlements. As most countries only have one or two CSDs, information had to be obtained from CSDs internationally as well as from the CSD in South Africa, namely Strate Ltd. The research was limited to evaluating a proposed model for securities settlements using blockchain technologies within a CSD of traditional CSD instruments, such as bonds, money markets and equities.

Due to the rapid developments and innovation in this area of technology specifically, this research was carried out within a two-year period without re-evaluating the latest available information and developments on Blockchain technology. No software application was developed in this study, as the primary aim of the study was focused on addressing broad-based principles to apply the use of Blockchain technologies for securities settlements.
