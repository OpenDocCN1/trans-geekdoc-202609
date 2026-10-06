# 7.2 Strengths and Weaknesses of Different PUF Designs Physical Unclonable Functions 159

TABLE 7.2 Strengths and Weaknesses of Different PUF Designs
| ARCHITECTURE | WEAKNESS | STRENGTH |
| :--- | :--- | :--- |
| Ring Oscillator PUF Arbiter PUF | Environmental vulnerability Delay path must be identical | Easy to design and fabricate (Partly) Resistance against machine learning attack |
| SRAM PUF | Low number of CRPs | Good statistical properties |
| TERO PUF | Need further investigations | Environmental toughness |
| Public PUF | Need further investigations | No secret info |

accepts only particular challenges, making it very challenging to get all of them, or only a limited amount of challenges every second, slowing down the attack by many orders of magnitude [60].

The best defensive technique is to make the PUF more resilient to external threats, effectively reducing aggressive attacks to the same level as passive attacks. There are two: first, CRPs can be kept secret by encryption. Alternatively, we may select a (healthy) PUF configuration with several CRPs that are enough to regenerate one [30].

In a more complex attack, the adversary uses machine learning techniques to conduct a prediction attack and simulate challenge-response pairs, using previously challenged response as feedback to train the machine learning model. Again, attacks of CRPs are expected to carry successful attacks. One approach to addressing attacks is to improve the robustness of the PUF architecture by the spatial nonlocality. Unfortunately, in the end, this technique has proven unsuccessful. Another solution was to use cryptographic methods to use machine learning to tackle situation attacks. This strategy was successful but ignored the design of the PUF, opening the field for side-channel attacks. A physical defense can be used to prevent aggressive and semi-invasive side-channel attacks. [30].

Higher robustness can be accomplished by making the PUF software robust to specific environmental changes, and the software of the PUF used decreases the probability of noninvasive side-channel attacks. Choosing the right PUF architecture is, therefore, essential. Finally, the PUF must be paired with an effective authentication protocol to incorporate an automated solution.

# 7.12 CONCLUSION

This chapter explained the brief history of PUF technology, its working, and various types of PUF circuits and architecture. We also discussed the multiple sources of security threats and how to mitigate them. The chapter also emphasized the applications of PUFs in various domains that have been pointed out, along with challenges faced by the technology. PUFs circuits can be a useful tool in designing embedded systems as well as for IoT systems. Commercially, IoT products are utilizing PUFs, for example, SRAM PUFs and buffers, for security enhancement. Despite covering so much ground, there are many challenges, and therefore active research is going on in this field.

New techniques and state-of-the-art approaches to secure PUFs are being proposed regularly, and this is a growing research area [61, 62]. Some of the solutions recently indicated the consistent evolution of novel PUF design, which is gaining fame, in direction of focus on security necessities. ASIC-based PUF interface, which is gaining fame, is due to their custom architecture and therefore not suitable for low-cost IoT situations. However, an alternate PUF design strategy targeting IoT devices can be an answer this problem. PUF based solutions are being increasingly adopted in commercial IoT applications. The credit of such widespread acceptability is due to the intrinsic nature of the SRAM PUF, catering to every prevalent electronic product. The number of IoT