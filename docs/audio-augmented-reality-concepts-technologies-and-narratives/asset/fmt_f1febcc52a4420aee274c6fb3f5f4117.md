
[Figure 2.7](#chapter02.xhtml#f2_7) presents the relationship between these four concepts, lateralised, externalised, acousmatic and attached sounds. A lateralised sound (playing inside the user’s head) can be either acousmatic or attached depending on the context. For example, a voice over is usually considered as acousmatic, or without having a physical origin, although we hear it as coming from inside our head. However, we are usually so accustomed to headphone listening with lateralised sounds and voices that we consider the sound to exist somewhere else, either in the ‘aether’ or coming from the computer or mobile phone screen thanks to the ventriloquism or ‘magnetisation’ effect (see [Chapter 4](#chapter04.xhtml)). An example of an attached sound playing inside the head, in turn, could be a physiological sound, an internal voice, or perhaps a character inside one’s skull.

![Figure 2.7Acousmatic and attached sounds as lateralised and externalised](images/fig2_7.jpg)

[Figure 2.7](#chapter02.xhtml#f2-7)Acousmatic and attached sounds as lateralised and externalised

## 2.12 Six degrees of freedom

AAR is not just about virtual sounds embedded in the real world; it is also about moving through the environment. Movement enhances the sense of presence (Järvinen, [2017](#chapter02.xhtml#r28)), and with binaural systems, registering movements helps externalisation of virtual sounds, making them appear to really coexist with the reality (Roginska, [2018](#chapter02.xhtml#r52); Brandenburg, et al., [2023](#chapter02.xhtml#r13)). Whereas the auditory display is the primary *output* interface in AAR, movement is often the primary *input* interface; events and interactions are triggered based on users location and movements.

In the XR world, the concept ‘degrees of freedom’ is essential. It is an engineering concept referring to different movements that are possible for an object in a given space (Paterson and Llewellyn, [2022](#chapter02.xhtml#r47)). In AAR, where the user—the ‘object’ in this case—is seldom physically restricted to move in the environment, the degrees of freedom usually refer to the system’s ability to track the head of the user and adjust the binaurally reproduced virtual soundscape accordingly.

If the binaural application was designed for a static user who keeps their head straight forward all the time, the virtual soundscape could be spatially fixed, utilising 0 degrees of freedom. If the user remains still, the illusion of virtual sounds coexisting with the reality may sound very plausible, *Séance* (see Chapter 5.4.) being a good example. In a similar application, a virtual sound that was attached to an object 2 metres to the left would appear as coming from that object 2 metres to the left. However, should the user decide to turn their head, the soundscape would turn with it, and the virtual sound would no more be aligned with the object.

To make the soundscape stay fixed even when turning the head, the system should be able to track in *three degrees of freedom* or *3DoF*. The three degrees in this case refer to orientation in Euler angles, or rotational movement: pitch, yaw, and roll. For the system to allow 3DoF, the user’s head must be tracked with sensors so that when the head turns, the virtual soundscape counter-rotates; the virtual sound would appear as staying attached to the object.

Now, if the experience is able to track both the user’s movement through space and head movements, we have *six degrees of freedom*, or *6DoF* (see [Figure 2.8](#chapter02.xhtml#f2_8)). The three additional degrees are translational movement in Euclidean space along the x axis (left and right), y axis (front and back), and z axis (up and down) (Mazuryk and Gervautz, [1999](#chapter02.xhtml#r37)). Now, the virtual soundscape can be spatially updated to match with the user’s movements and it appears as staying fixed relative to the environment.

![Figure 2.8Six degrees of freedom (6DoF)](images/fig2_8.jpg)

[Figure 2.8](#chapter02.xhtml#f2-8)Six degrees of freedom (6DoF)

It is worth noting, that the term 3DoF can sometimes refer to translational movement—movement along the x, y, and z axes—though this usage is rare in the context of virtual audio.

## 2.13 Conclusion

AAR can be understood as a framework of multiple technologies and applications with a shared goal: enhancing the perception and understanding of reality. This is accomplished by merging virtual auditory content with the environment, erasing and replacing sounds, and improving hearing. This chapter introduced some of the key concepts and terminology related to AAR, which will be referenced throughout the book. The next chapter explores reality, immersion, and interactivity, establishing the foundation for augmented reality applications and experiences.

## References

1.  [Aalborg University](#chapter02.xhtml#re_ref7) (2024) ‘Audio Only VR for Blind Gamers’, Aalborg University’s Research Portal. Available at: [https://vbn.aau.dk/en/projects/audio-only-vr-for-blind-gamers](https://vbn.aau.dk/en/projects/audio-only-vr-for-blind-gamers) (Accessed: 3 December 2024).

2.  [Akın, A.T. and Cömert, Ç](#chapter02.xhtml#re_ref8). (2023) ‘The Development of an Augmented Reality Audio Application for Visually Impaired Persons’, Multimedia Tools and Applications, 82 (11), pp. 17493–17512. Available at: [https://doi.org/10.1007/s11042-022-14134-x](https://doi.org/10.1007/s11042-022-14134-x).

3.  [Albrecht, R., Väänänen, R. and Lokki, T.](#chapter02.xhtml#re_ref9) (2016) ‘Guided by Music: Pedestrian and Cyclist Navigation with Route and Beacon Guidance’, Personal and Ubiquitous Computing, 20 (1), pp. 121–145. Available at: [https://doi.org/10.1007/s00779-016-0906-z](https://doi.org/10.1007/s00779-016-0906-z).

4.  [Azuma, R.](#chapter02.xhtml#re_ref10) (1997) ‘A Survey of Augmented Reality’, Presence: Teleoperators and Virtual Environments, 6 (4), pp. 355–385. Available at: [https://doi.org/10.1162/pres.1997.6.4.355](https://doi.org/10.1162/pres.1997.6.4.355).

5.  [Azuma, R.](#chapter02.xhtml#re_ref11) et al. (2001) ‘Recent Advances in Augmented Reality’, IEEE Computer Graphics and Applications, 21 (6), pp. 34–47. Available at: [https://doi.org/10.1109/38.963459](https://doi.org/10.1109/38.963459).

6.  [Bach-y-Rita, P. and Kercel, S.W.](#chapter02.xhtml#re_ref12) (2003) ‘Sensory Substitution and the Human–Machine Interface’, Trends in Cognitive Science, 7 (12), pp. 541–546. Available at: [https://doi.org/10.1016/j.tics.2003.10.013](https://doi.org/10.1016/j.tics.2003.10.013).

7.  [Brandenburg, K.](#chapter02.xhtml#re_ref13) et al. (2023) ‘Implementation of and Application Scenarios for Plausible Immersive Audio Via Headphones’, in Audio Engineering Society Convention 155, Audio Engineering Society. Available at: [https://www.aes.org/e-lib/browse.cfm?elib=22308](https://www.aes.org/e-lib/browse.cfm?elib=22308) (Accessed: 25 November 2023).

8.  [Brandenburg, K. and Sloma, U.](#chapter02.xhtml#re_ref14) (2024) ‘Conversation with Matias Harju, May 23’.

9.  [Chion, M.](#chapter02.xhtml#re_ref15) (1994) Audio-Vision: Sound on Screen. Columbia University Press.

10.  [Choueiri, E.](#chapter02.xhtml#re_ref16) (2018) ‘Binaural Audio Through Loudspeakers’, in A. Roginska and P. Geluso (eds) Immersive Sound: The Art and Science of Binaural and Multi-Channel Audio. Routledge, pp. 124–179.

11.  [Cliffe, L.](#chapter02.xhtml#re_ref17) (2022) Audio Augmented Objects and the Audio Augmented Reality Experience. PhD thesis. University of Nottingham. Available at: [https://eprints.nottingham.ac.uk/69795/](https://eprints.nottingham.ac.uk/69795/).
