
Note that `62443-4-1` and `2` were both published in `2018` in February and August respectively and that although `62443-4-1` has been adopted by BSI, `62443-4-2` has yet to be.

`62443-2-1` defines the requirements for a Cyber Security Management System (CSMS) and although it has used a different term, in its first paragraph, BSI (2010) `62443-2-1` refers to the output of `27001` as a CSMS. The `62443` CSMS however, reverses the information security triad and precedes it with safety, to become Safety, Availability, Integrity and Confidentiality, in recognition of the HSE implications of cyber security in an industrial environment. In the same way as `27001`, it requires the implementation of risk management and review processes that support the CSMS lifecycle.

The fundamental differences in approach between `27001` and `62443` become more apparent in `62443-3-3` (although some of the content in this part of the standard is destined for inclusion in `62443-1-1` as the standard develops) which describes the use of security vectors, a term credited to Gilsinn and Schierholz (2010). A parallel is drawn between SLs (Security Levels) and SILs (Safety Integrity Levels), the latter being the measure applied in `61508`, and supporting standards, which include `61511`.

![image](images/fig3.9.jpg)

**Fig 3.9.**Associated safety and security standards.

SLs are determined during the `62443` risk assessment process; as part of the network segregation controls, the IACS network is divided into zones, each zone grouping system components that require the same level of protection. An SL-T (Target Security Level) is assigned to the zone according to the level of protection required, i.e.

•SL 0: No specific requirements or security protection necessary

•SL 1: Protection against casual or coincidental violation

•SL 2: Protection against intentional violation using simple means with low resources, generic skills and low motivation

•SL 3: Protection against intentional violation using sophisticated means with moderate resources, IACS-specific skills and moderate motivation

•SL 4: Protection against intentional violation using sophisticated means with extended resources, IACS-specific skills and high motivation

Each system component is then assessed against security requirements defined in the standard to assess its SL-C (Security Level Capability). If the SL-C is greater than or equal to the zone’s SL-T then no further controls are required, but if it is of a lower value then either the residual risk must be formally accepted or further controls are required. It is likely that there will be a mix of SL-Cs for the systems in any particular zone, in which case it is the lower value SL-Cs that must be addressed to achieve the SL-T.

For verification, the system can be inspected, audited or otherwise security tested and an SL-A (Actual Service Level) determined by the inspector. Risks are managed using these three values: ST-T, SL-C and SL-A.

`62443-2-1` intends that SLs will ultimately provide a quantitative approach to addressing security for a system or a component part of it. This is presumably a long-term aspiration, not to be realised until more data becomes available through wider adoption of the standard. It is also intended to deliver a repeatable model and be applicable to both devices and countermeasures.

The safety risk analysis process defined by `50129` is concerned with safety hazards and how often they occur rather than security threats. It explores the consequence of any failure in terms of accidents, near-misses or ‘safe failures’ and whether the outcome is acceptable in safety terms. It uses SILs as “a means of matching the qualitative approaches (to avoid systematic failures) with the quantitative approach (to control random failures), as it is not feasible to quantify systematic failures” ((BSI, 2003) 50129). Systematic failures are those introduced by human error at some point during the system lifecycle, and are managed by process, e.g. quality management. Random failures result from the reliability of hardware components, which can be calculated from known failure rates and expressed as a THR (Tolerable Hazard Rate). The safety level requirement expressed by the SIL is a combination of process and an acceptable THR.

Adopting the use of SLs and assuming similarity to SILs and SLs could be misleading in that the two measures are somewhat dissimilar. As Braband (2016) advocates, the probabilistic approach applied to SILs does not really apply to SLs and IT security as it is not possible to rely on statistical data or experience as the threat landscape can change immediately and without warning.

The similarities and the differences between safety and security risk assessment are explored in some depth by Braband and Schäbe (2016) who assert that the risk assessment processes for safety and security are very similar and that it would be logical to apply the same process for each. The article goes on to identify that safety risk assessments defined by international safety standards are based on ‘probability’ whereas security risk assessments are based on ‘likelihood’. ISO (2009) defines these two different words respectively as “a measure of the chance of occurrence expressed as a number between 0 and one, where 0 is impossibility and one is absolute certainty” and “the chance of an event happening”. Safety standards are based on the concept that there is a probability that a dangerous failure will occur at some point in time and that the chance of it happening can be measured. The failures could be systematic or random; the occurrence of random failures can be calculated and for systematic failures there is a commonly agreed upon set of countermeasures that is generally accepted across the industry. Likelihood is far less precise and relies far more on subjective opinion. The reason that safety can deliver more objectivity is that the safety environment is slow to change and much can be learned from past experience. Security is far more volatile and can change from day to day. This can frequently be observed in information technology as new vulnerabilities emerge and the threat landscape changes. A good example of the latter can be observed on the NCSC’s Alerts and Advisory web pages (NCSC, 2018b):

![image](images/page_098.jpg)

State actors are likely to be the most capable and resourceful attackers, which could raise the SL-T requirement of any potential target to SL 4 to give it any possible chance of being able to withstand an attack.

Kriaa *et al.* (2015) take a similar stance to Braband and Schäbe, recognising that safety hazards are relatively stable over time and feedback from analysts on previous accidents is reliable, whilst security attributes are less predictable. This situation makes it more difficult for security analysts to assess and particularly, quantify, potential scenarios. It is observed that the use of quantitative approaches is more widely adopted in the field of safety but is not so readily accepted within security disciplines.

Nevertheless, the development of the `62443` series continues and 2018 has seen the publication of two more standards: `62443-4-1` in February and `62443-4-2` in August, both addressing supply chain factors. [Figure 3.10](#chapter3.xhtml#fig3.10) shows their relationship with the rest of the set.
