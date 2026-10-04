
![Figure 4.2: Timeline diagram representing speech translation past and future.](graphic/converted/b_9783110648195-004_fig_002.png)

Figure 4.2: Timeline diagram representing speech translation past and future.

Speech translation is an architectural cluster of three technologies: speech recognition, language translation, and speech synthesis. Automatic translation of speech requires the automation of these three technologies with seamless integration to complete the task. All of these have their own difficulties. Compared to text translation, speech translation is far more complex due to the involvement of colloquial expressions, the influence of nativity in speech, and presence of ungrammatical phrases. Considering the complex nature of the translation work, the research community initially started work in limited domain involving simple conversation and gradually progressed to more advanced jobs.

Many disparities in healthcare have been reported in the literature and communication difficulties have been identified as one of the most important factors ([Jacobs et al., 2001](#bodymatter-004.xhtml#b_9783110648195-004_ref_015); [Fassil, 2000](#bodymatter-004.xhtml#b_9783110648195-004_ref_013); [Bischoff et al., 2003](#bodymatter-004.xhtml#b_9783110648195-004_ref_005); [Flores et al., 2005](#bodymatter-004.xhtml#b_9783110648195-004_ref_014)). Owing to these, several efforts in the direction of speech translation have been carried out in the medical domain. Due to enormous challenges in this field, all projects have been focused toward specific communication in this domain and are biased toward a few user profiles. Not much success has yet been achieved in the medical domain, and for long there has been debate regarding success of technology-oriented spoken language techniques in the field which is more receptive to the varying needs of principle users that may be doctor, patient, or other healthcare service provider. [Table 4.1](#bodymatter-004.xhtml#b_9783110648195-004_tab_001) outlines the projects working for speech translation in the medical domain. Some of them are available as a fully functional system in the commercial market. The domain specified in the table highlights their usability and also identifies the intended users of the system.

Table 4.1:Projects working on speech translation in the medical domain.

| System || Developers || Domains || Languages |
| --- | --- | --- | --- |
| CCLNC || MITLIncoln Lab  
(Lee et al., 2002) || Doctor–patient dialogue || English, Korean |
| --- | --- | --- | --- |
| MASTOR || IBM Yorktown Heights (Zhou et al., 2003) || Medical emergencies || English, Mandarin |
| Speechalator || Carnegie Mellon University (Waibel et al., 2003) || Medical interviews || English, Arabic |
| Laser ACTD || Carnegie Mellon University (Schulz et al., 2004) || Doctor–patient dialogue || English, Thai |
| No name || SRI Menlo Park CA  
([Kathol et al., 2005](#bodymatter-004.xhtml#b_9783110648195-004_ref_018)) || First medical exchanges || English, Pashto |
| Transonics || University of Southern California ([Ettelale et al., 2005](#bodymatter-004.xhtml#b_9783110648195-004_ref_012)) || Doctor–patient dialogue || English, Farsi |
| Accultran || A-life Medical Inc, San Diego CA  
(Heinze et al., 2006) || Doctor–patient dialogue || English, Spanish |
| S-MINDS || Sehda Inc, Mountain View CA ([Ehsani et al., 2006](#bodymatter-004.xhtml#b_9783110648195-004_ref_011)) || Medical disaster recovery || English, Korean |
| Converser || Spoken Translation, Berkeley CA [www.Spokentranslation.com](http://www.Spokentranslation.com) /products/healthcare || Pharmacy, emergency, physical therapy, admissions, obgyn, oncology || English, Spanish |
| MASTOR || IBM Yorktown Heights domino.watson.ibm.com/comm/pr.nst/pagesnews 20061013_mastor.html || Medical-oriented conversations with members of the Iraqi security forces, in hospital settings and during daily interactions with Iraqi citizens || English, Arabic(Iraqi and MSA) |
| MedSLT || ISSCO, University of Geneva [www.issco.unige.ch/projects/medst/](http://www.issco.unige.ch/projects/medst/) || Headache, chest pain, abdominal pain || English, French, Japanese, Finnish, Spanish, Greek |
| S:MINDS || fluential Inc, Sunnyvale Ca [www.fluentialinc.com/therapy.swf](http://www.fluentialinc.com/therapy.swf) || Radiology, physical therapy || English, Spanish |
| MediBabble || University of California, San Francisco http:/medibabble.com/ || Cardiovascular, pulmonary || Spanish, Cantonese, Mandarin, Russian, and Haitian Creole |
| BabelDr || University of Geneva  
([P. Bouillon et al., 2017](#bodymatter-004.xhtml#b_9783110648195-004_ref_006)) || Abdomen || French to Arabic |

## 4.3 Speech translation technology: an overview

Automatic speech translation is a cluster of three major technologies in the NLP domain. The overall process requires the understanding of spoken utterance followed by its translation into the target language, consistent with the language grammar rules. This complete process would create a pathway for patients with limited knowledge of the language at the service provider. It can be achieved by sequence execution of three technologies, that is, ASR, machine translation (MT), and TTS. The pipeline is depicted in [Figure 4.3](#bodymatter-004.xhtml#b_9783110648195-004_fig_003). This technological cluster will also help the patients with visual or any physical impairments to communicate with the doctors or the care providers as well as to connect with the digital world to take a more direct role in self-health and treatment. Spoken language communication needs a system that can recognize, interpret, and respond.

![Figure 4.3: Pipeline architecture of speech-to-speech translation.](graphic/converted/b_9783110648195-004_fig_003.png)

Figure 4.3: Pipeline architecture of speech-to-speech translation.

### 4.3.1 Speech production and perception

One of the major concerns in the field of automatic speech processing is the gap between the performance of machine and human. Incorporating knowledge into the machine about how humans produce and perceive sounds will help improve the performance of a machine. Before moving into the details of using technology to remove the language barrier, the study of the anatomy of speech production must be understood. Automating the whole process of speech processing and understanding is a complicated task, not only due to domain complexities but also due to the complexities associated with the vocal machine of the human system. The system will require handling the vocal tract (VT) characteristics of individual, accent due to nativity, background noise, and also the microphone characteristics in addition to coping with the ambiguity of the language and nongrammaticality of spoken conversations.

Human voice production is a complex system that is capable of producing several distinct sounds. Lungs, larynx, and VT combine to constitute the human voice production system. VT, that is, oral/nasal cavity, soft/hard palate, tongue, lips, jaw, and teeth form the most important organ affecting the speech production. The respiratory (lungs) and the laryngeal (larynx) subsystems provide the source (air pressure) for speech signal. The articulatory subsystem works upon the generated signal to produce different phones. These sound units can be categorized as voice, unvoiced, or plosives depending upon the articulators responsible for their production. The varying nature of sound units creates challenges for their automated processing.
