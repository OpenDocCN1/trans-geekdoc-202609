
# Registration Phase

In this phase, the user’s initial information will be collected to enable him/her to use the system. At the time of registration (either online or offline), a set of different topics is provided to the user, for example, childhood memories, current hobbies, dream holidays, etc. The user may have to choose `m` out of `n` topics (where `m` and `n` are the system parameters decided by the domain people).

For each chosen topic, the user has to provide a story with sufficient information (again, this is application and domain-dependent). If there is insufficient information, the system will prompt the user again to input more information. The stories provided by the user create a personalized information space for the user (similar to a static password).

Now authors demonstrate this feature through an example. Here, the user describes his/her childhood experience.

> “When I think about it, I had a real good childhood. Believed in the things some kids are supposed to believe in like Santa Clause and the tooth fairy which made it exciting. Always had a good Christmas with toys laid out like Santa had been there and when I lost a tooth, when I put it under my pillow, I would get money for it. I enjoyed playing childhood games, playing with my cousin and the other kids. I was crazy about Barbie dolls and had a lot of them and Barbie houses. I had a bike and a scooter. I had the love and care of my family and knew it. I loved jumping on our trampoline and playing outside. Well, life was great back then when I was a kid! I could look any way I wanted to and had no real worries. I didn't have it hard; I had it good and easy. I hate ghosts and scary stories. I was always afraid of dark places and being alone.”

Based on the given story, the system will extract keywords and information from every possible sentence or the system manager may extract the keywords from the given story. The following are the possible keywords and information:

*   Santa
*   Tooth fairy
*   Jumping on trampoline
*   Hate ghosts and scary stories
*   Afraid of dark places and being alone
*   Crazy about Barbie dolls. Had Barbie houses.
*   Love to play with cousin and friends.

Based on this information, the system may either create or link with the existing image database. The keywords and the information will be embedded in an image and implicitly presented to the user during the authentication process. The user has to click the right object to represent his/her answer. It has been shown that this information is easy to remember than complex passwords.

# Segmentation Phase

In this phase, the system works on creating a visualized image of a user's logged answers (keywords) which lead to an interface behavior. The tool used in visualization is geared towards improving the system design so that the technique realized within the system development is perfectly segmented.

As reported by Merch and White (2003), the image relationships functions are categorized into three sets: (A) functions expressing a far/distant relation to the text; (B) functions expressing a close relation to the text; and (C) functions going beyond the text. Applying these sets identifies the level of implicitly for each image. The semantic variants of this concept can be developed quickly and with little effort by the system developer. It is true, therefore, to state that implementing a new segment of technology will take specialized skills, time as well as many resources that many organizations do need to take into consideration.

# The Authentication Phase

First, a user may request access to the system by presenting his user name and the level of access required. This may be sent as a plain text. Depending on the level of access required, the system might request `k` out of `m` areas chosen by the user during the registration process. For each chosen area, the server may pick a random keyword extracted from the user’s story. For each keyword, the server may again pick a random image from the image database that contains an object which has the chosen text attribute.

Similar to Kerberos, a session key `S` is derived from the correct clickable area through a function `f(I)`. The server will choose a random number `p` and then encrypt `p` with the session key `S` and transmit `(Image, S[p], f(I))` to the mobile device. The client application then displays the image. Using the stylus or a mouse, the user needs to choose the correct “clickable area”. Then, based on the function `f(I)`, the image `I` and the area the user clicked, the client will generate a key `K`. The function `f(I)` is chosen in such a way that `S = K` if and only if the user and the server have exactly the same area of interest in the image. The user then decrypts `S[p]` to obtain the random number. He then transmits `p+1` to the server for authentication and to the next level. In this way, the user is authenticated implicitly and no confidential information is exchanged over the network. When the server is executing the last question in the authentication process, instead of encrypting a pseudo random number, it will pick a session key and encrypt it with the derived key. When the client decrypts it, he receives an implicit message from the server to use this session key for transmission. This procedure not only authenticates a user implicitly, but also exchange a session key implicitly.

Figure 6 illustrates the IPAS Client/Server authentication process steps for registered users which are as follows:

1.  The user sends an authentication (Login) request to the IPAS server using his/her mobile phone device or computer.
2.  The server checks the user’s registration status. If the user is not registered, then the authentication process fails (END); however, for registered users, it proceeds to the next step.
3.  The system checks the user’s access level according to the user’s pre-set IPAS domains and the implicit level of an object in the image (in the case of a payment process, access control will check the payment amount in order to make a decision).
4.  The IPAS authentication image is created and sent to the user according to the output of Step 3.
5.  The user receives a response from the server with the IPAS image. If the user clicks an incorrect object to represent his/her password, then he/she needs to resend the authentication request (i.e. return Step 1). However, if the user clicks on the correct object in the IPAS image, the user will be authenticated (Login).

![Figure 6. IPAS Client/Server authentication process](i/ch003.f06.png)

In this section, we presented the high-level flow chart of the IPAS authentication process between the user (client) and server (cloud). The above steps show the interaction architecture between client and server for authentication purposes. Our future directions will be focused on designing a detailed software architecture/prototype using UML (Unified Modeling Language) which will include software engineering and mathematical models. We consider IPAS to be a complex project with many stages; therefore, more scientific models and system processes will be left for future design, development, and implementation. In addition, a more analytical model of IPAS and its domains’ performance indicators will be covered in later stages. Rapid developments in communication/network media and mobile device capabilities will help us to form future work of the remaining stages of IPAS.

# Database and Image Characteristics
