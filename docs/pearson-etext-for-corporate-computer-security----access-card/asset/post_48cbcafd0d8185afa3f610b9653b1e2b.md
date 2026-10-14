
## Mandatory and Discretionary Access Control
- Mandatory access control (MAC)
  - No departmental or personal ability to alter access control rules set by higher authorities
- Discretionary access control (DAC)
  - Departmental or personal ability to alter access control rules set by higher authorities
- MAC gives stronger security but is very difficult to implement

## Multilevel Security
- Resources are rated by security level
  - Public
  - Sensitive but unclassified
  - Secret
  - Top secret, etc.
- People are given the same clearance level
- Some rules are simple
  - People with a secret clearance cannot read top-secret documents
- Some rules are complex
  - What if a paragraph from a top-secret document is placed in a secret document?
- Access control models have been created to address multilevel security
  - Will not discuss the models because not pertinent to corporations

Figure 5-2 Military and National Security Organization Access Controls
(Study Figure)

## Multilevel Security
Documents and other resources vary in sensitivity. Typically, military and national security organizations have a multilevel security system that rate documents by sensitivity. Some documents will be completely public, while others will be sensitive but unclassified (SBU). Beyond this, there are several levels of classifications, such as secret and top secret.

Giving access to classified information requires careful thought. Obviously, if someone does not have a security clearance, he or she should not be allowed to read a top-secret document. Other issues require more thought. For instance, what if a single paragraph from a classified document is copied into a sensitive but unclassified document? To cope with such issues and to deal with various access situations, organizations that use multilevel security must follow complex access control models. This book focuses on corporate security, where traditional multilevel security does not work for many reasons. Consequently, we will not discuss access control models.

## Test Your Understanding
- 2. a. Distinguish between mandatory access controls and discretionary access controls.
- b. What is multilevel security?
- c. What are SBU documents?
- d. Do they need to be considered in access controls?
- e. Why are access control models needed?

## In the News
### MoviePass Reset
In 2019 it was discovered that media company MoviePass had intentionally reset at least some of its users' passwords in an effort to slow down its own discount movie ticket system.² MoviePass claimed that this was only done to a small number of "power users" in an effort to stop abuse of the system. MoviePass users paid $10 per month to watch unlimited movies. However, MoviePass claimed that a small number of users were abusing the system and purchasing multiple tickets for the same showing and sharing their card with non-MoviePass users. Regardless of the circumstances, preventing users from accessing a service they paid for was at least ethically questionable. Then it was discovered that MoviePass had also implemented a "trip wire" that would limit the number of tickets for certain popular movie releases to a few hundred thousand users. The remaining users would see a message saying there were no more tickets available.

### Facebook’s Biometric Lawsuit
In 2019 a judge said a multibillion-dollar class-action lawsuit against Facebook could proceed.³ The lawsuit claims that Facebook's facial recognition technology that helps users identify friends in uploaded photos violates Illinois's privacy laws. The lawsuit is a major setback for Facebook because it depends on the facial recognition application and it has plans to expand its use of biometrics. If successful, the lawsuit would have a chilling effect on other tech companies that are using or intend to use biometric data obtained from their users.

### Facial Recognition Laws
In 2019 three cities passed laws prohibiting facial recognition. San Francisco and Oakland, California, and Somerville, Massachusetts, all have ordinances banning facial recognition applications within their city limits.⁴ Lawmakers who sponsored the bills said facial recognition is a violation of people's basic human rights. They note that the software could be used to discriminate against women and people of color and potentially be used to limit free speech. They note the chilling effects seen after the implementation of China's new social credit and surveillance systems. Interestingly, San Francisco is the home to many of the largest technology companies that could greatly benefit from facial recognition applications including Facebook, Alphabet (Google), Pinterest, Twitter, Yelp, and LinkedIn.

### Surveillance 1984 to 2019
In 2019 a UK man was fined £90 ($110) for "disorderly behavior" after covering up his face while he walked past a new facial recognition system being implemented by London's Metropolitan Police.⁵ The man said he didn't want to be photographed or be in the system. Officers weren't sure which law he was violating, so they issued him a generic citation for disorderly behavior. Ironically, George Orwell, author of the famous novel 1984, which depicts an oppressive surveillance state, is buried just an hour and a half away from where the man was issued his citation. London's Metropolitan Police must have read Orwell's 1984, but they're way behind schedule.

² Catie Keck, "MoviePass Changed User Passwords and Activated a ‘Trip Wire’ to Prevent User Access," Gizmodo, August 9, 2019. https://gizmodo.com/moviepass-changed-user-passwords-and-activated-a-trip-w-1837103557.

³ Melissa Locker, "In a Big Blow to Facebook, Court Lets Class-Action Lawsuit over Biometric Data Move Forward," Fast Company, August 8, 2019. www.fastcompany.com/90387974/facebook-lawsuit-class-action-over-biometrics-proceeds.

⁴ Melanie Ehrenkranz, "Another U.S. City Moves to Ban Face Recognition, Citing Threats to Free Speech and Civil Rights," Gizmodo, July 31, 2019. https://gizmodo.com/fourth-u-s-city-bans-facial-recognition-citing-threat-1836858623.

⁵ Katyanna Quach, "Let’s Check In with Our Friends in England and, Oh Good, Bloke Fined after Hiding Face from Police Mug-Recog Cam," The Register, May 16, 2019. www.theregister.co.uk/2019/05/16/police_face_recognition.

## Forcing Your Finger
In 2019 a federal district court judge in Massachusetts, Judith Dein, found that law enforcement has the right to force your finger onto a biometrically protected iPhone or any other device to see if it unlocks it.⁶ Law enforcement agents for the Bureau of Alcohol, Tobacco, Firearms and Explosives (ATF) received a warrant to force suspect Robert Brito-Pina’s fingers onto an iPhone. However, if a *passcode* were used to secure the phone, Brito-Pina would not be required to provide it. The Fifth Amendment protects individuals from being forced to give self-incriminating evidence.

## 5.2 Physical Access and Security
### 5.2 Describe physical building and computer security.
Many attacks take place remotely over networks. However, attackers can also walk into a building, walk up to a computer, and then steal or hack it. Although network access control is crucial, IT security professionals need to understand physical access control for buildings, high-security zones within buildings, and individual computers. We will base this section on ISO/IEC 27002’s⁷ Security Clause 11 (*Physical and Environmental Security*).

### Risk Analysis
Security clause 11 assumes that risk analysis has already been done. IT security professionals need to begin with an understanding of risks that exist at the levels of buildings, secure zones within buildings, and computers. A bank obviously needs far stronger perimeter security than a university, and a server room needs stronger security than an ordinary office area.

### ISO/IEC 11.1: Secure Areas
Security Clause 11 has two main security categories. The first is 11.1, **Secure Areas**, which is concerned with securing physical areas, including entire buildings, equipment rooms, office areas, delivery and shipping areas, and general public areas. Main Security Category 11.1 has six controls.

**PHYSICAL SECURITY PERIMETER** It is important to control building entry points. Ideally, there will be a **single point of entry**. In addition, the walls that separate the building from the outside should be sound, and there should be no gaps through which people can enter. If security requirements call for a staffed reception area, it should be staffed constantly.

Although a single point of entry facilitates control, every building has **emergency exits** that can be opened for escape whenever justified. If the intruder has a confederate in the building, the confederate can open one of these doors to let in the attacker. Consequently, emergency exits should be alarmed, monitored (preferably with cameras), and tested frequently.

In all cases, security provisions must be compatible with fire codes. Most importantly, it is illegal to lock fire exits to bar escape.

⁶ Kieren McCarthy, “FYI: Yeah, the Cops Can Force Your Finger onto a Suspect’s iPhone to See If It Unlocks, Says Judge,” *The Register*, April 24, 2019. www.theregister.co.uk/2019/04/24/judge_forced_finger_toiphone_unlock.

⁷ The current version is ISO/IEC 27002:2013. The 2013 is the date of the last update. Until 2007, ISO/IEC 27002 was known as ISO/IEC 17799. The renumbering was done as part of a comprehensive program to develop new security standards under the 27000 heading.
