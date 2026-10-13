
## Shoulder Surfing Attacks

Shoulder surfing is basically watching over the shoulders of users to see or record their password with the help of a camera when a user is entering their password. IPAS is immune to this kind of attack by providing a new implicit object as a password at each time of authentication.

## Replay Attacks

Keylogging or key spyware cannot be used to break the IPAS scheme and mouse tracking software also cannot hack IPAS, as it is fully protected against them.

## IPAS Limitations

Like any system, IPAS has certain limitations due to various components, such as network, human, and system hardware issues. The most common complexities which may be considered as a hindrance in the IPAS process and may influence system performance are:

*   **Limited or short coverage of network and wireless communication** in some locations where the user (client) cannot communicate with the server or service provider, especially in the payment authentication process.
*   **Limited storage, a screen display or processing capabilities** of the client’s mobile device which may cause a delay in dealing with the IPAS image.
*   **Frequent logins by users** may result in an IPAS image being repeated on a particular level, for example, using IPAS to log in to a mobile phone with a one-minute auto-lock when the user logs in more than 30 times in one hour. This scenario requires many images to represent the user’s password which may cause an overload on the server-side.
*   Some argue that even implicit objects can be guessed.

Researchers tried to minimize the above limitations by applying different solutions, which may help to stabilize the use of IPAS. The first solution is to provide optional secondary methods for users to switch to either text-based or token-based methods when they face difficulties dealing with the IPAS primary authentication method. The second solution depends on the IPAS domains, which help users to choose the implicit level of their objects within the IPAS image, as explained in the previous section. Finally, to avoid an image being repeated, the user can update his/her profile with real-time personal images (taken with his own camera) and change the keywords, which represent his/her password, from time to time. As we aim to introduce an authentication scheme that is immune to common attacks such as replay attacks (internal and external) and/or shoulder surfing, the above-mentioned solutions help to minimize the side effects of, but not remove, the above mentioned IPAS limitations.

## SUMMARY

In this chapter, the authors presented IPAS and its applications, which solve the security drawbacks of other authentication schemes and provide an acceptable balance between security and anonymity for multimedia data in a cloud environment.

On the authentication side, IPAS has many features as follows:

*   **Immune to replay attacks and shoulder surfing**, which are considered main problems in other authentication systems and graphical-based password authentication systems such as PassPoint by providing a new image at every time of authentication in an implicit form.
*   **Flexible** compared with other graphical-based authentication techniques where the user can switch to a text-based password if they experience difficulties in dealing with the image by applying the intelligent text-based authentication option.
*   **Domains of IPAS** provide different levels of security according to the user’s needs.
*   **Can be implemented in mobile and non-mobile devices**. In general, IPAS is a client-server authentication which works on personal computers and mobile phones.
*   **IPAS will improve the security level of Multimedia data in the cloud.**
*   **IPAS is a fast and flexible authentication scheme for mobile users.**
*   **The computation cost of the proposed scheme is acceptable and adjusts to different security levels.**

## CONCLUSION

Cloud computing technology provides cost-saving and flexibility of services for users. With the explosion of multimedia data, more and more data owners would outsource their personal multimedia data on the cloud. Privacy preserving is a hot topic in cloud computing in recent years. Once users’ data are a leak, the negative impact can be huge. Therefore, the development of privacy-preserving technology is the key factor for cloud computing. IPAS can provide the first layer of protection and easy access for user’s Multimedia data on the cloud environment. It is quite desirable and helpful in some sensitive applications such as mobile banking, multimedia data and online purchasing.

## REFERENCES

Almuairfi, S., Veeraraghavan, P., & Chilamkurti, N. (2011). IPAS: Implicit Password Authentication System. *Proceedings 2011 IEEE Workshops of International Conference Advanced Information Networking and Applications (WAINA)*, pp. 430-435, March 22-25, 2011 doi: 10.1109/WAINA.2011.36

Dirik, A. E., Memon, N., & Birget, J. C. (2007, July). Modeling user choice in the PassPoints graphical password scheme. *Proceedings of the 3rd symposium on Usable privacy and security* (pp. 20-28). Pittsburgh, PA: ACM.

Yang, Z., Huang, Y., Li, X., Wang, W., Wu, F., Zhang, X., ... & Li, W. (2018). Efficient, secure data provenance scheme in multimedia outsourcing and sharing. *Computers, Materials, & Continua*, 56(1), 1–17.

Geir, M. K. (2013, October). Privacy enhanced mutual authentication in LTE. *Proceedings 2013 IEEE 9th International Conference on Wireless and Mobile Computing, Networking and Communications (WiMob)* (pp. 614-621). IEEE.

Birget, J. C., Hong, D., & Memon, N. (2006). Graphical passwords based on robust discretization, *Information Forensics and Security*. *IEEE Transactions*, 1(3), 395–399.

Haddad, Z. J., Taha, S., & Saroit, I. A. (2017). Anonymous authentication and location privacy, preserving schemes for LTE-A networks. *Egyptian Informatics Journal*, 18(3), 193–203. doi:10.1016/j.eij.2017.01.002

Hamandi, K., Sarji, I., Chehab, A., Elhajj, I. H., & Kayssi, A. (2013, March). Privacy enhanced and computationally efficient HSK-AKA LTE scheme. *Proceedings 2013 27th International Conference on Advanced Information Networking and Applications Workshops*. (pp. 929-934). IEEE.

Wang, C., Zheng, W., Ji, S., Liu, Q., & Wang, A. (2018). Identity-based fast authentication scheme for smart mobile devices in body area networks. *Wireless Communications and Mobile Computing*, 2018.

Islam, A., Por, L. Y., Othman, F., & Ku, C. S. (2019). A Review on Recognition-Based Graphical Password Techniques. *Proceedings Computational Science and Technology* (pp. 503–512). Singapore: Springer. doi:10.1007/978-981-13-2622-6_49

Lashkari, A. H., Saleh, R., Towhidi, F., & Farmand, S. (2009, December). A complete comparison on pure and cued recall-based graphical user authentication algorithms. *Proceedings 2009 Second International Conference on Computer and Electrical Engineering* (Vol. 1, pp. 527-532). IEEE.

Masrom, M., Towhidi, F., & Lashkari, A. H. (2009, October). Pure and cued recall-based graphical user authentication. *Proceedings 2009 International Conference on Application of Information and Communication Technologies* (pp. 1-6). IEEE.

Merch, E. E., & White, M. D. (2003). A taxonomy of relationships between images and text. *The Journal of Documentation*, 59(6), 647–672. doi:10.1108/00220410310506303

Ogundoyin, Sunday Oyinlola. (2018). An autonomous lightweight conditional privacy-preserving authentication scheme with provable security for vehicular ad-hoc networks. *International Journal of Computers and Applications*, 1–16.

Parne, B. L., Gupta, S., & Chaudhari, N. S. (2019). PSE-AKA: Performance and security enhanced authentication key agreement protocol for IoT enabled LTE/LTE-A networks. *Peer-to-Peer Networking and Applications*, 12(5), 1156–1177. doi:10.1007/s12083-019-00785-5
