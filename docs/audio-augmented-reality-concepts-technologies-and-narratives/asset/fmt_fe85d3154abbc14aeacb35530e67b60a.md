
Latencies below 60 or 50 milliseconds (ms) are usually considered as imperceptible in most virtual audio cases, while less than 30 ms being nearly unnoticeable (Brungart, Kordik and Simpson, [2006](#chapter07.xhtml#r240); Brandenburg et al., [2023](#chapter07.xhtml#r238)). In practice, those numbers can be achieved if the tracking system is very fast, such as `OptiTrack` or `VIVE Tracker`, audio rendering is well optimised and running on a powerful computer with a small audio buffer, and as many connections are tethered as possible. However, many AAR applications cannot run on such specifications. For example, even if head orientation tracking using an IMU tracker is relatively fast with a 10 ms latency (Supper, [2021](#chapter07.xhtml#r275)), the location tracking system may introduce over 100 ms latencies. Luckily, snappy head-orientation tracking is generally more critical, while fast location tracking becomes crucial only when virtual sounds are nearby.

Audio rendering adds additional delays, as discussed in Chapter 7.3. Complex auditory scenes place greater demands on the computer and software, often resulting in larger audio buffer sizes and increased latency. Finally, if wireless audio transmission to headphones is required, it may add significant latency. Professional wireless systems can achieve latencies under 1 millisecond. Some low-latency Bluetooth codecs, such as `aptX LL` and `LHDC LL`, offer delays of 30–40 ms, whereas standard Bluetooth codecs can introduce delays exceeding 200 ms, which can significantly impact the user experience (Katz, [2024](#chapter07.xhtml#r257)). With all that, if the system can reach motion-to-sound latency of around 100 ms, even that can be considered rather good in terms of maintaining plausibility (Lindau, [2009](#chapter07.xhtml#r260)).

The ventriloquism effect, where virtual sounds ‘magnetise’ to plausible physical objects, can compensate for some dynamic errors (see Ahrens, [2019](#chapter07.xhtml#r229)). However, practical experience suggests that this tolerance is limited, and the sound cannot deviate significantly. If tracking is unstable and the virtual sound appears to drift around the physical object, the illusion is likely to break more easily.

## 7.8 Complete systems and standards

Although it is currently not possible to purchase a complete 6DoF AAR system anywhere, at least to the knowledge of the author, there are a few proprietary systems made with companies that produce AAR content. However, even their systems are not complete: while they pack technology in a well-thought and reliable form, the authoring pipeline or tracking system may still be relying on 3rd party tools and complex workflows.

Partial solutions are or will be available for purchase, and the first-ever standard for interactive, immersive audio, `MPEG-I`, should have been published in 2025 when this book comes out. The standard, a joint effort of multiple companies, aims to unify and stabilise audio rendering across devices. It enables 6DoF within audio scenes and supports both binaural and loudspeaker setups. `MPEG-I` is scalable and able to optimise rendering resolution for mobile devices with limited processing capacity. Built on `MPEG-H` coding, it supports channel-based and object-based audio (OBA) as well as higher order ambisonics (HOA), and introduces multi-point HOA (Herre et al., [2024](#chapter07.xhtml#r251)). In terms of AAR, one important feature is the possibility to input parameters, such as room reverberation time (RT60), in order to match the virtual acoustics with the real environment (Herre and Disch, [2023](#chapter07.xhtml#r250)).

Another recently published standard and codec particularly interesting in terms of AAR is `IVAS`. As a joint effort of multiple telecommunications and technology companies, the codec enables, for instance, ad-hoc capture of a spatial auditory scene—such as people around the meeting table—by using a single mobile device. Also, multiple audio streams from each participant’s remote locations can be spatialised at the end user’s device (Bruhn, Multrus and Varga, [2022](#chapter07.xhtml#r239); IVAS Codec Public Collaboration Contributors, [2023](#chapter07.xhtml#r255)).

It remains to be seen how widely these standards will be adopted by hardware and software companies, how effectively they will simplify and unify production pipelines, and how they will enable seamless cross-platform content distribution. Still, their existence already reflects the growing recognition of the importance of virtual and spatial audio in the industry.

## 7.9 Conclusion

The number of possible technologies to realise AAR may seem overwhelming. Choosing the right approach is always a challenging process with a risk that testing one technology takes money and time, and in the end, turns out not to be the best. The lack of ready-made, complete systems openly available for content creators—apart from geolocated AAR platforms—is likely to slow down ideas from getting into AAR applications and experiences. This chapter has hopefully provided guidance for practitioners in selecting the right components for a given project, reducing the need for extensive trial and error, while also offering a glimpse into the technological potential and opportunities available in AAR.

## References

1.  [Ahrens, A.](#chapter07.xhtml#re_ref229) et al. (2019) ‘Sound Source Localization with Varying Amount of Visual Information in Virtual Reality’, PLOS ONE, 14 (3), p. e0214603. Available at: [https://doi.org/10.1371/journal.pone.0214603](https://doi.org/10.1371/journal.pone.0214603).

2.  [Albrecht, R., Lokki, T. and Savioja, L.](#chapter07.xhtml#re_ref230) (2011) ‘A Mobile Augmented Reality Audio System with Binaural Microphones’, in Proceedings of Interacting with Sound Workshop: Exploring Context-Aware, Local and Social Audio Applications. New York, NY, USA: Association for Computing Machinery (IwS ’11), pp. 7–11. Available at: [https://doi.org/10.1145/2019335.2019337](https://doi.org/10.1145/2019335.2019337).

3.  [ALPS](#chapter07.xhtml#re_ref231) (2018) ‘ALPS – Acoustic Localisation Positioning System’. Available at: [https://alps.fi/](https://alps.fi/) (Accessed: 26 November 2024).

4.  [Amfitech](#chapter07.xhtml#re_ref232) (2024) ‘AMFITRACKTM, AmfiTrack’. Available at: [https://www.amfitrack.com](https://www.amfitrack.com) (Accessed: 26 November 2024).

5.  [Arena, F.](#chapter07.xhtml#re_ref233) et al. (2022) ‘An Overview of Augmented Reality’, Computers, 11 (2), p. 28. Available at: [https://doi.org/10.3390/computers11020028](https://doi.org/10.3390/computers11020028).

6.  [Armbruster, S.](#chapter07.xhtml#re_ref234) (2024) ‘Conversation with Matias Harju, March 7’.

7.  [Bederson, B.B.](#chapter07.xhtml#re_ref235) (1995) ‘Audio Augmented Reality: A Prototype Automated Tour Guide’, in Conference Companion on Human Factors in Computing Systems – CHI ’95. Denver, Colorado, United States: ACM Press, pp. 210–211. Available at: [https://doi.org/10.1145/223355.223526](https://doi.org/10.1145/223355.223526).

8.  [Bimber, O. and Raskar, R.](#chapter07.xhtml#re_ref236) (2005) Spatial Augmented Reality: Merging Real and Virtual Worlds. Wellesley, Massachussets: A K Peters.

9.  [Boquet, G., Vilajosana, X. and Martinez, B.](#chapter07.xhtml#re_ref237) (2024) ‘Feasibility of Providing High-Precision GNSS Correction Data Through Non-Terrestrial Networks’, IEEE Transactions on Instrumentation and Measurement, 73, pp. 1–15. Available at: [https://doi.org/10.1109/TIM.2024.3453319](https://doi.org/10.1109/TIM.2024.3453319).

10.  [Brandenburg, K](#chapter07.xhtml#re_ref238). et al. (2023) ‘Implementation of and Application Scenarios for Plausible Immersive Audio Via Headphones’, in Audio Engineering Society Convention 155, Audio Engineering Society. Available at: [https://www.aes.org/e-lib/browse.cfm?elib=22308](https://www.aes.org/e-lib/browse.cfm?elib=22308) (Accessed: 25 November 2023).
