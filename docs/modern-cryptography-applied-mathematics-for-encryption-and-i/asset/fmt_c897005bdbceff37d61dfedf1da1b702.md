
Governments have an interest in regulating the import and export of cryptographic equipment and software. The export issue may be more obvious, so let’s begin with that. If a nation has cryptographic software or hardware that is highly secure, that government may want to limit its export to other countries. It is not in any government’s interest to hand other nations its means to secure communications. Import restrictions may not be so obvious, however. One major reason for such restrictions is the fear of cryptographic backdoors (see [Chapter 18](#part0029.xhtml#ch18)). Essentially there is a concern that if products are imported from foreign nations, those products could contain backdoors that subvert security.

###### COCOM and the Wassenaar Arrangement

There have been attempts to regulate and standardize the export of various products considered to be of strategic military value, including both munitions and cryptographic products. One early attempt was the Coordinating Committee for Multilateral Export Controls (COCOM), which consisted of Australia, Belgium, Canada, Denmark, France, Germany, Greece, Italy, Japan, Luxemburg, The Netherlands, Norway, Portugal, Spain, Turkey, United Kingdom, and the United States. Other nations did not join the committee but cooperated with the standards it set: Austria, Finland, Hungary, Ireland, New Zealand, Poland, Singapore, Slovakia, South Korea, Sweden, Switzerland, and Taiwan.

In 1991, COCOM decided to allow the export of mass-market software that implemented cryptography. In 1995, the successor to COCOM, the Wassenaar Arrangement on Export Controls for Conventional Arms and Dual-Use Goods and Technologies (often simply called the Wassenaar Arrangement), was created.^([5](#part0026.xhtml#ch15note5a))

**Note**

The name comes from the town where the original agreement was reached in 1995. The town of Wassenaar is a suburb of The Hague in the Netherlands. As of this writing, 41 countries have signed the Wassenaar Arrangement.

The Wassenaar Arrangement followed most of the COCOM recommendations but provided a specific exception for the use of mass-market and public domain cryptographic software. It also included a personal use exception that allowed the export of products that were for the user’s personal use (such as encrypting their laptop hard drive).

In 1998, the Wassenaar Arrangement was revised to allow the following:

  ![image](Images/image00484.jpeg)   Export for all symmetric cryptography products using keys up to 56 bits

  ![image](Images/image00484.jpeg)   Export for all asymmetric cryptography products using keys up to 512 bits

  ![image](Images/image00484.jpeg)   Export for elliptic curve–based asymmetric products using keys up to 112 bits

  ![image](Images/image00484.jpeg)   Export of mass-market products (software and hardware) using keys up to 64 bits

**Note**

In 2000, the Wassenaar Arrangement lifted the 64-bit limit for mass-market cryptographic products.

###### Specific Government Regulations

The European Union (EU) regulates cryptography exports under the “Council Regulation (EC) No 1334/2000 setting up a Community regime for the control of exports of dual-use items and technology.” The EU essentially follows the Wassenaar Arrangement with a few exceptions:

  ![image](Images/image00484.jpeg)   Export from one EU member nation to another is relaxed, with the notable exception of cryptanalysis products.

  ![image](Images/image00484.jpeg)   Exceptions can be applied to exporting to certain nations including Canada, Australia, Japan, and the United States.

Australia regulates the export of cryptographic products via the Defense and Strategic Goods List. This regulation is notable in that it includes a specific exemption for public-domain software. In 2001, Australia passed the Cybercrime Act of 2001, which included a clause requiring the release of encryption keys or decrypting the data if a court order was issued. Australia passed its Defense Trade Control Act of 2012, which describes “dual use goods” (products with both military and civilian use) and includes segments on electronics and telecommunication. However, its requirements on encryption are not very clear, and some are concerned that it could lead to criminalizing the teaching of cryptography.^([6](#part0026.xhtml#ch15note6a))

China first implemented the Commercial Use Password Management Regulations in 1999, which requires a license from the government before cryptographic functions can be imported or exported. In 2000, the Chinese government clarified this order, indicating that the order refers to products that have cryptography as a core function. Products such as mobile phones and web browsers, for which cryptographic functions are ancillary, are exempted.

Several nations require a license to use encrypted communications. In Iran, a license is required to use cryptography for any communications. Israel requires a license from the government to export or import cryptographic products. Pakistan requires government approval for the sale or use of cryptography products.

India, under the Information Technology Act 2000, does not require a license, but any organization or individual must cooperate with any agency of the government to assist in decrypting data if requested.

Although Russia has signed the Wassenaar Arrangement, its laws go a bit further. A license is required to import cryptography products manufactured outside of Russia. Exporting cryptography requires government approval.

Belarus has strict regulations regarding the import and export of cryptography. A license is required for the design, production, sale, repair, and operation of cryptography. Along with other countries, Belarus may not recognize a personal use exception.

**Tip**

Many of us use encrypted hard drives on our personal computers. If you plan to travel internationally, be sure to check the laws of the countries you will be traveling through before you go to determine if you must comply with particular laws or regulations. It may be necessary for you to take a separate laptop that does not include encryption.

Belgium passed the Law on Information-Science Crime in 2000, in which Article 9 allows a court to issue an order to a person who is suspected of having “special knowledge” of encryption services to provide information to law enforcement on how to decrypt data. This means that if a suspect has encrypted data, the court can order the vendor of the cryptography product to provide assistance in decrypting the data. Failure to comply can result in 6 to 12 months of incarceration.

**Note**

There has been a great deal of debate regarding how to handle evidence that has been encrypted by parties suspected of criminal activity. Currently, the United States has no laws compelling anyone to reveal encrypted data or to assist in decrypting the data, although there has been discussion of creating such laws, which now exist in several other countries.

#### Cryptography and Malware

Malware, even cryptographic malware, may seem to be an unrelated topic for this chapter. How does malware relate to military applications of cryptography? As cyber-warfare becomes increasingly real, malware that uses cryptography in one form or another has become a common weapon used by governments and other entities.

The term “cryptovirology” is sometimes applied to the study of how cryptography is combined with malware. One application of cryptography with malware is the use of encryption to protect a virus from detection; this is an example of an “armored virus.”^([7](#part0026.xhtml#ch15note7a)) One of the first armored viruses was the Cascade virus, which was discovered in the late 1980s. This clearly demonstrates that using encryption to bolster viruses is not a new technique.

Malware encryption is done not only to prevent detection, but also to make it difficult to analyze the malware. To use encryption the malware needs at least three components:
