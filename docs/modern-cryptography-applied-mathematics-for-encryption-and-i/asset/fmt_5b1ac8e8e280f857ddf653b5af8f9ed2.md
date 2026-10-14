
In December 1839, Poe published a challenge in the Philadelphia periodical `Alexander’s Weekly Messenger`. In that challenge, he stated that he could solve any single-substitution cipher than readers could submit. His challenge stated

        It would be by no means a labor lost to show how great a degree of rigid method enters into enigma-guessing. This may sound oddly; but it is not more strange than the well known fact that rules really exist, by means of which it is easy to decipher any species of hieroglyphical writing—that is to say writing where, in place of alphabetical letters, any kind of marks are made use of at random. For example, in place of A put % or any other arbitrary character—in place of B, a \*, etc., etc. Let an entire alphabet be made in this manner, and then let this alphabet be used in any piece of writing. This writing can be read by means of a proper method. Let this be put to the test. Let any one address us a letter in this way, and we pledge ourselves to read it forthwith—however unusual or arbitrary may be the characters employed.^([1](#part0010.xhtml#ch02note1a))

From December 1839 to May 1840, Poe was able to solve all the ciphers that readers submitted—except one. Since that time, however, various analysts have determined that this cipher was simply a set of random characters and not a legitimate example of cipher text.

* * *

#### Cryptography Comes of Age

The various ciphers used in the 19th through the early 20th centuries were certainly more complex than the ciphers of earlier times. However, they were still ciphers that could be decrypted manually, with pencil and paper. The 20th century moved cryptography toward encryption related to devices and alternative methods of encryption.

##### Enigma

Contrary to popular misconceptions, the `Enigma` is not a single machine, but a family of machines. The first version was invented by German engineer Arthur Scherbius near the end of World War I. It was also used by several different militaries, not only the Nazi Germans.

Some military texts encrypted using a version of Enigma were broken by Polish cryptanalysts Marian Rejewski, Jerzy Różycki, and Henryk Zygalski. The three basically reverse-engineered a working Enigma machine and then developed tools for breaking Enigma ciphers, including one tool called the `cryptologic bomb`.

The `rotors` were the core of the Enigma machine—disks that included 26 letters arranged in a circle, with several rotors aligned with one another. Essentially, each rotor represented a different single-substitution cipher—you can think of the Enigma as a sort of mechanical poly-alphabet cipher. After the operator was given a message in plain text, he typed the message into the Enigma. For each letter that was typed in, Enigma would provide a different cipher text based on a different substitution alphabet. The recipient would type in the cipher text to retrieve the plain text, but only if both Enigma machines had the same rotor settings. [Figure 2-1](#part0010.xhtml#ch02fig01) shows an Enigma machine.

![Images](Images/image00546.jpeg)

* * *

**FIGURE 2-1    An Enigma machine**

###### Enigma Variations

The Enigma models included several variations:

![image](Images/image00484.jpeg)   Enigma A, the first public Enigma

![image](Images/image00484.jpeg)   Enigma B

![image](Images/image00484.jpeg)   Enigma C

![image](Images/image00484.jpeg)   Enigma B, used by United Kingdom, Japan, Sweden, and others

![image](Images/image00484.jpeg)   Navy Cipher D, used by the Italian Navy

![image](Images/image00484.jpeg)   Funkschlüssel C, used by the German Navy beginning in 1926

![image](Images/image00484.jpeg)   Enigma G, used by the German Army

![image](Images/image00484.jpeg)   Wehrmacht Enigma I, a modification to the Enigma G, used extensively by the German military

![image](Images/image00484.jpeg)   M3, an improved Enigma introduced in 1930 for the German military

Other systems were either derived from Enigma or were similar in concept, including the Japanese system codenamed GREEN by American cryptographers, the SIGABA system, NEMA, and others.

###### Alan Turing

I cannot tell the story of Enigma without at least mentioning Alan Turing, who is famous for leading the team that was able to crack the Enigma version used by the German Navy during World War II—a story that has been immortalized in the book `Alan Turing: The Enigma` and the movie `The Imitation Game`. During World War II, Turing worked for the Government Code and Cipher School that operated out of Bletchley Park, located 50 miles northwest of London. The mansion and 58 acres were purchased by MI6 (British Intelligence) for use by the Code and Cipher School. A number of prominent people worked at Bletchley Park, including mathematicians Derek Taunt and Max Newman, and chess champion Hugh Alexander.

Turing’s impact on the field of cryptography is profound. He led the British team responsible for attempting to break the German naval Enigma. He worked to improve the pre-war Polish machine that would find Enigma settings. He was successful, and MI6 was able to decipher German naval messages. This work was considered highly classified. They feared that if the Germans realized that the Enigma had been compromised, they would change how they communicated. So intelligence gathered via Turing’s team was kept a closely guarded secret, and when it needed to be shared with others (such as military commanders), a cover story was given to account for the source of the information. Many sources claim that Turing’s work at Bletchley Park shortened the war by at least two years, saving millions of lives.

**Note**

Alan Turing was a mathematician and an accomplished marathon runner as well. He also was a key figure in the development of computer science. Among his most notable achievements, he developed a test to determine if a machine was indeed sentient—that test is known as the `Turing Test`.

The work at Bletchley Park was kept in strict secrecy, but in the decades since the war, many details have been declassified and are now available to the public. Turing’s team was by no means the only team working at Bletchley Park. Various “huts,” or buildings, on the grounds were used for various purposes. Turing and his team worked on the Naval Enigma in Hut 8. In Hut 6, a team worked on the Army and Air Force Enigmas. Hut 7 concentrated on Japanese codes and intelligence. Other huts were used for intelligence work and support work (such as communications and engineering), and Hut 2 was a recreational hut where the workers at Bletchley could enjoy beer, tea, and relaxation.

The work at Hut 8 centered on use of a `bombe`, an electromechanical device that helped to determine what settings the Enigma machine was using. The initial design used at Bletchley was created by Turing and later refined by others such as Gordon Welchman, a British mathematician.

The work at Bletchley was kept top secret, and much of the equipment and documents were destroyed at the end of the war. Even close relatives did not know what their family at Bletchley worked on. Today it is home to a museum with extensive displays of cryptography history, including Enigma machines.

##### SIGABA

`SIGABA` was an encryption machine used by the U.S. military from World War II through the 1950s. The machine, a joint effort of the U.S. Army and Navy, was developed specifically to overcome weaknesses found in other rotor systems, such as Enigma. You can find detailed specifications for this machine today, but some of the operating principles remained classified until the year 2000. SIGABA was patented (6,175,625), filed on December 15, 1944, but the patent remained classified until 2001. [Figure 2-2](#part0010.xhtml#ch02fig02) shows a picture of a SIGABA machine.

![Images](Images/image00547.jpeg)

* * *

**FIGURE 2-2    SIGABA machine**
