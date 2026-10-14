
## FORENSICS IV

## Chapter 23

## Digital Visual Media Forensics

Raahat Devender Singh

## Contents

- 23.1 Introduction to the Forensic Applications of Images and Videos................665
- 23.1.1 Photographic Evidence: Origin and History .....................665
- 23.1.2 Video Data as Evidence and the Impact of CCTV ...............666
- 23.1.2.1 Video Evidence: Origin Story .....................666
- 23.1.2.2 CCTV and Surveillance .....................667
- 23.2 Visual Evidence and the Fallacy of Infallibility ...........669
- 23.3 Indispensability of Visual Evidence and the Need for Authentication....672
- 23.4 Digital Visual Media Forensics .....................672
- 23.4.1 Evidence Collection, Recover, and Repair.....................673
- 23.4.2 Forensic Evidence Enhancement.....................674
- 23.4.3 Evidence Authentication .....................675
- 23.4.3.1 The Concept of Identifying Traces.....................675
- 23.4.3.2 Source Identification and Evidence Provenance......676
- 23.4.3.3 Content Authentication and Tamper Detection......677
- 23.4.3.4 Evidence Enhancement and Evidence Tampering...677
- 23.4.4 Hidden Data Detection .....................677
- 23.4.4.1 Specific or Targeted Steganalysis.....................678
- 23.4.4.2 Universal or Blind Steganalysis.....................678
- 23.4.4.3 Caveats of Blind Steganalysis.....................680
- 23.4.4.4 Steganalysis Tools .....................680
- 23.4.5 Identification and Interpretation................................................681
- 23.4.5.1 Object Identification.......................................................681
- 23.4.5.2 Evidence Interpretation.....................................................681
- 23.5 Variants of Digital Visual Media Forensics ...........................................682
- 23.5.1 Active and Passive Forensics...................................................682
- 23.5.2 Blind and Non-Blind Forensics..................................................683
- 23.6 Source Identification and Evidence Provenance .......................................684
- 23.6.1 Source Camera Identification (SCI) ...........................................684
- 23.6.1.1 Image/Video Acquisition Pipeline ...........................................685
- 23.6.2 Classes of Source Camera Identification .......................................686
- 23.6.2.1 Source Model or Device Class Identification ..............................687
- 23.6.2.2 Individual Source or Specific Device Identification .....................688
- 23.6.3 Pattern Noise-Based Source Camera Identification.............................690
- 23.6.3.1 Limitations of PRNU-Based SCI..............................................691
- 23.6.3.2 Modified Noise Pattern Estimation: SPN Based Analysis ....................692
- 23.6.4 Blind Source Camera Identification............................................693
- 23.7 Integrity Verification and Content Authentication...................................693
- 23.7.1 Content Authentication: Active-Non-Blind Methods ...........................694
- 23.7.1.1 Timestamp Analysis Based Authentication...................................694
- 23.7.1.2 Limitations of Timestamp Based Authentication............................694
- 23.7.1.3 Digital Signatures and Watermarks for Content Authentication.............695
- 23.7.1.4 Limitations of Digital Signature and Watermark Based Content Authentication...695
- 23.7.2 Passive-Blind Methods for Content Integrity Verification....................696
- 23.7.2.1 Hash Value Analysis .......................................................696
- 23.7.2.2 Metadata Analysis..........................................................697
- 23.7.2.3 Hex Editor Analysis........................................................697
- 23.8 Passive-Blind Methods of Tamper Detection.........................................698
- 23.8.1 Kinds of Forgeries in Digital Images and Videos ..............................698
- 23.8.1.1 Copy-Paste Forgeries.......................................................699
- 23.8.1.2 Upscale-Crop...............................................................700
- 23.8.1.3 Frame-Insertion/Removal/Replication........................................701
- 23.8.1.4 Temporal Splicing...........................................................701
- 23.8.2 Specialized Tamper Detection Techniques.......................................703
- 23.8.2.1 Detection of Frame-Insertion/Removal/Replication .........................703
- 23.8.2.2 Detection of Temporal Splicing.............................................706
- 23.8.2.3 Detection of Copy-Paste Forgeries..........................................707
- 23.8.2.4 Detection of Upscale-Crop ....................................709
- 23.8.2.5 Detection of Green-Screening................................709
- 23.9 Anti-Forensics and Counter Anti-Forensics................................710
- 23.9.1 Image and Video Anti-Forensics ....................................710
- 23.9.2 Image and Video Counter Anti-Forensics ............................711
- 23.10 Summary ............................................................711
- References and Resources ................................................712

> Truth will ultimately prevail where there is pains taken to bring it to light.
>
> —George Washington

## 23.1 Introduction to the Forensic Applications of Images and Videos

As unbiased and unmediated proofs of occurrence of events, photographs and videos are an especially privileged kind of evidence. In this section, we discuss the origin and history of the forensic applications of photographic and video evidence, so as to better understand how they came to be the significant and compelling sources of information they are today.

### 23.1.1 Photographic Evidence: Origin and History

Photographs have had a 174 year-long history of sustained forensic use, the origin of which can be traced back to the early nineteenth century, i.e., almost as soon as the invention of photography itself. When French inventor Joseph Nicéphore Niépce created the world’s first permanent camera and made a photograph in 1826 or 1827, several attempts were made to commercialize the process of photography. It was only after the invention of daguerreotype cameras by French photographer and artist Louis-Jacques-Mandé Daguerre, that it became possible to mass-produce cameras, and as soon as these cameras became publicly available in 1839, photography’s potential for the documentation and identification of criminal classes was recognized. Earliest instances of photographic documentation of prisoners dates back to 1843–1844 in Belgium and 1851 in Denmark. By 1848, police in Liverpool and Birmingham were photographing criminals, and by the mid 1850s, English and French authorities had begun encouraging their law enforcement agencies to photograph prisoners, mostly to prevent escapes and document recidivism.

By the 1870s, photographs had become a widely accepted means of forensic identification; professional photographers were being employed to take posed portraits, also known as portraitures, of criminals. However, despite their widespread use, portraitures were not standardized using the same lighting, scale, and angles, and were thus futile for identification purposes, a fact that was first realized in 1888 by Alphonse Bertillon, a French police officer and biometrics researcher. Bertillon then suggested anthropological studies of profiles and full-face shots (aka mug shots) for reliable documentation and identification of criminals.

Photographs were finding similar utility for the documentation of crime scenes and scenes of accidents as well. The earliest documented instance in that regard can be found in an 1852 American photographic journal that described an accident in which the victim’s lawyer used pictures taken at the scene of the accident, and which from their realism explained the entire event much more clearly than any sort of oral description could.

Over time, with advancements in photography and camera manufacturing techniques, photographs (of people, objects, and events) became a generally accepted form of evidence, both inside and outside the justice system.

### 23.1.2 Video Data as Evidence and the Impact of CCTV

A photograph captures a single moment in time, which essentially makes it an arrested representation of reality. A video on the other hand, presents a record of an event over a period of time, which makes it a much more potent forensic evidence that still photographs.

In the olden days, video evidence was hard to come by. But in the modern world with ubiquitous surveillance and a plethora of digital multimedia capture devices where hardly any event of significant worth escapes the watchful eye of a camera, video data has emerged as a truly indispensable source of information. During a criminal trial for instance, video evidence, when available, is regarded as a particularly inculpatory kind of evidence. Unlike other forensic evidence like DNA and fingerprints, which are circumstantial in nature and require further inference, videos provide a first-hand account of an event, and its realism makes us confident in its authority as a witness.

### 23.1.2.1 Video Evidence: Origin Story

The first documented instance of use of video footage during a criminal trial was the Rodney King case of 1991. On the night of March 3, 1991, King, a taxi driver in Los Angeles, was assaulted by Los Angeles Police Department officers following a high-speed car chase. A witness named George Holliday videotaped much of the beating from his balcony and sent the footage to a local news station (Figure 23.1).

The footage was used during the ensuing trial in 1992 where the officers were charged with assault with a deadly weapon and use of excessive force. Despite the video evidence, the jury failed to convict the officers and they were acquitted of the charges brought against them. Within hours of the acquittals, angry LA citizens
