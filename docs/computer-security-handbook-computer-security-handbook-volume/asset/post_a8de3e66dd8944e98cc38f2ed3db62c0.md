
Information we do not know but possess by selling, buying, bartering, giving, receiving, and trading until we ultimately control, transport, and use them. We have incorrectly defined possession if we include only the protective efforts for confidential material.

We protect the possession of information by preventing people from unauthorized taking, from making copies, and from holding or controlling it—whether confidentiality is involved or not. The loss of possession of information also includes the loss of control of it, and may allow the new possessor to violate its confidentiality at will. Thus, loss of confidentiality may accompany loss of possession. But we must treat confidentiality and possession separately to determine what actions criminals might take and what controls we need to apply to prevent their actions. Otherwise, we may overlook a particular threat or an effective control. The failure to anticipate a threat and vulnerability is one of the greatest dangers we face in security.

Controls that can protect the possession of information include using copyright laws, implementing physical and logical usage limitations, preserving and examining computer audit logs for evidence of stealing, inventorying tangible and intangible assets, using distinctive colors and labels on media containers, and assigning ownership to enforce accountability of organizational information assets.

The severity of loss of possession varies with the nature of the offense. In a worst-case scenario, a criminal may take information, as well as all copies of it, and there may be no means of recovery—either from the perpetrator or from other sources such as paper documentation. In a less harmful scenario, a criminal might take information for some period of time but leave some opportunity for recovery at a moderate cost. In the least harmful situation, an owner could possess more than one copy of information, leaving open the possibility of recovery from other sources (e.g., backup files) within a reasonable period of time.

## 3.2.7 Conclusions about the Six Elements.

We need to understand some important differences between integrity and authenticity. For one, integrity deals with the intrinsic condition of information, while authenticity deals with the extrinsic value or meaning relative to external sources and uses. Integrity does not deal with the meaning of the information with respect to external sources, that is, whether the information is timely and not obsolete. Authenticity, in contrast, concerns the question of whether information is genuine or valid and not out of date with respect to its potential use. A user who enters false information into a computer possibly has violated authenticity, but as long as the information remains unchanged, it has integrity. An information security technologist who designs security into computer operating systems is concerned only with application information integrity because the designer cannot know if any user is entering false information. In this case, the security technologist's job is to ensure that both true and false information remain whole and complete. It is the information owner, with guidance from an information security advisor, who has the responsibility of ensuring that the information conforms to reality—in other words, that it has authenticity.

Some types of loss that information security must address require the use of all six elements of the framework model to determine the appropriate security to apply. Each of the six elements can be violated independently of the others, with one important exception: A violation of confidentiality always results in loss of exclusive possession, at the least. Loss of possession, however—even exclusive possession—does not necessarily result in loss of confidentiality.

Other than that exception, the six elements are unique and independent, and often require different security controls. Maintaining the availability of information does not necessarily maintain its utility; information may be available but useless for its intended purpose, and vice versa. Maintaining the integrity of information does not necessarily mean that the information is valid, only that it remains the same or, at least, whole and complete. Information can be invalid and, therefore, without authenticity, yet it may be present and identical to the original version and, thus, have integrity. Finally, who is allowed to view and know information and who possesses it are often two very different matters.

Unfortunately, the written information security policies of many organizations do not acknowledge the need to address many kinds of information loss. This is because their policies are limited to achieving CIA. To define information security completely, the policies must address all six elements presented. Moreover, to eliminate (or at least reduce) security threats adequately, all six elements need to be considered to ensure that nothing is overlooked in applying appropriate controls. These elements are also useful for identifying and anticipating the types of abusive actions that adversaries may take—before such actions are undertaken.

For simplification and ease of reference, we can pair the six elements into three double elements, which should be used to identify threats and select proper controls, and we can associate them with synonyms so as to facilitate recall and understanding:

- availability and utility → usability and usefulness
- integrity and authenticity → completeness and validity
- confidentiality and possession → secrecy and control

Availability and utility fit together as the first double element. Controls common to these elements include secure location, appropriate form for secure use, and usability of backup copies. Integrity and authenticity also fit together; one is concerned with internal structure and the other with conformance to external facts or reality. Controls for both include double entry, reasonableness checks, use of sequence numbers and checksums or hash totals, and comparison testing. Control of change applies to both as well. Finally, confidentiality and possession go together because, as discussed, they are interrelated. Commonly applied controls for both include copyright protection, cryptography, digital signatures, escrow, and secure storage.

The order of the elements here is logical, since availability and utility are necessary for integrity and authenticity to have value, and these first four elements are necessary for confidentiality and possession to have material meaning.

## 3.3 WHAT THE DICTIONARIES SAY ABOUT THE WORDS WE USE.

CIA would be adequate for security purposes if the violation of confidentiality were defined to be anything done with information, if integrity were defined to be anything done to information, and if availability were to include utility, but these definitions would be incorrect and are not understood by many people. Information professionals are already defining the term “integrity” incorrectly, and we would not want to make matters worse. These definitions of security and the elements are relevant abstractions from Webster’s Third New International Dictionary and Webster’s Collegiate Dictionary, 10th edition.

Security—freedom from danger, fear, anxiety, care, uncertainty, doubt; basis for confidence; measures taken to ensure against surprise attack, espionage, observation, sabotage; resistance of a cryptogram to cryptanalysis usually measured by the time and effort needed to solve it.

Availability—present or ready for immediate use.

**Utility**—useful, fitness for some purpose.
**Integrity**—unimpaired or unmarred condition: soundness: entire correspondence with an original condition; adherence to a code of moral, artistic or other values; the quality or state of being complete or undivided: material wholeness.
**Authenticity**—quality of being authoritative, valid, true, real, genuine, worthy of acceptance or belief by reason of conformity to fact and reality.
**Confidentiality**—quality or state of being private or secret: known only to a limited few, containing information whose unauthorized disclosure could be prejudicial to the national interest.
**Possession**—act or condition of having or taking into one's control or holding at one's disposal; actual physical control of property by one who holds for himself, as distinguished from custody: something owned or controlled.

We lose credibility and confuse information owners if we do not use words precisely and consistently. When defined correctly, the six words are independent (with the exception that information possession is always violated when confidentiality is violated). They are also consistent, comprehensive, and complete. In other words, the six elements themselves possess integrity and authenticity, and therefore they have great utility. This does not mean that we will not find new elements or replace some of them as our insights develop and technology advances. (I first presented this demonstration of the need for the six elements in 1991 at the 14th U.S. National Security Agency/National Institute of Standards and Technology National Computer Security Conference in Baltimore.)

My definitions of the six elements are considerably shorter and simpler than the dictionary definitions, but appropriate for information security.

**Availability**—usability of information for a purpose
**Utility**—usefulness of information for a purpose
**Integrity**—completeness, wholeness, and readability of information and quality being unchanged from a previous state
**Authenticity**—validity, conformance, and genuineness of information
**Confidentiality**—limited observation and disclosure of knowledge
**Possession**—holding, controlling, and having the ability to use information

## 3.4 COMPREHENSIVE LISTS OF SOURCES AND ACTS CAUSING INFORMATION LOSSES.

The losses that we are concerned about in information security come from people who engage in unauthorized and harmful acts against information, communications, and systems, such as embezzlers, fraudsters, thieves, saboteurs, and criminal hackers. They engage in harmful using, taking, misrepresenting, observing, and every other conceivable form of human misbehavior. Natural physical forces such as air and earth movements, heat and cold, electromagnetic energy, living organisms, gravity and projectiles, and water and gases also are threats to information, as are inadvertent human errors.

Extensive lists of losses found in information security often include fraud, theft, sabotage, and espionage, along with disclosure, usage, repudiation, and copying. The first four losses in this list are criminal justice terms at a different level of abstraction from the last four and require an understanding of criminal law, which many information owners and security specialists lack. For example, fraud includes theft only if it is
