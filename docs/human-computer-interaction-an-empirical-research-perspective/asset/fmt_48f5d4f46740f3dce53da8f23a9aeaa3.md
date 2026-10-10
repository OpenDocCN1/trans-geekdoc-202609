
[Fig. 7.8](#Chp007_293-360_B9780443140969000130.xhtml#f0045) presents a scrolling concept for a right-handed user. On the keyboard's left, a touch strip is shown, but a wheel is just as appropriate. There are many implementation issues, such as scrolling sensitivity and support for up/down paging, but these are not explored here. Our point is simply that scrolling is an appropriate task for the non-dominant hand and that this is revealed in the model of bimanual control. See also Buxton and Myers [\[52\]](#Chp007_293-360_B9780443140969000130.xhtml#br0260).

![Figure 7.8 Scrolling interface example (sketch courtesy of Shawn Zhang).](images/B9780443140969000130/gr008.jpg)

[Figure 7.8](#Chp007_293-360_B9780443140969000130.xhtml#cf0320) Scrolling interface example (sketch courtesy of Shawn Zhang).

On a personal note, the idea of non-dominant hand scrolling was sufficiently appealing that I decided to re-engineer a Microsoft Intellimouse, separating the wheel assembly from the mouse. The new setup allowed operation of the mouse with the dominant hand while scrolling with the non-dominant hand, as seen in [Fig. 7.9](#Chp007_293-360_B9780443140969000130.xhtml#f0050)a for a right-handed user. This setup was used for numerous demos and presentations. Two such presentations were given in February 1998 during a visit to Microsoft in Redmond, Washington. The first audience was the "mouse group" of Microsoft's Hardware Ergonomics Group. The idea seemed provocative, so the team arranged an impromptu meeting later that day for the "keyboard group." I gave the same presentation again. The idea of non-dominant hand scrolling, as suggested in the model of bimanual control, was convincing. A new project was initiated within Microsoft. About two years later, Microsoft released the Office Keyboard. See [Fig. 7.9](#Chp007_293-360_B9780443140969000130.xhtml#f0050)b. On the left side, the device includes some power keys and a scrolling wheel (see arrow) – perfect for right-handed users.

![Figure 7.9 Non-dominant-hand scrolling. (a) The author's re-engineered Microsoft Intellimouse with the wheel on left side of the keyboard. (b) Microsoft Office Keyboard with scrolling wheel on the left side.](images/B9780443140969000130/gr009.jpg)

Figure 7.9 Non-dominant-hand scrolling. (a) The author's re-engineered Microsoft Intellimouse with the wheel on left side of the keyboard. (b) Microsoft Office Keyboard with scrolling wheel on the left side.

Variations of keyboards with left-side scrolling were subsequently released by Microsoft and other keyboard manufacturers, including Logitech. In the end, however, the momentum and popularity of the wheel mouse was just too much. The benefit of non-dominant-hand scrolling was insufficient to overcome the cost of learning a new interaction method. A satisfied user community could not be swayed toward a new interface paradigm.^([^(124)](#fn124))

In this section, we examined common GUI tasks and patterns of bimanual skill. Two important observations emerged: First, current desktop systems favour left-hand mouse use, and, second, scrolling is well supported by delegation to the non-dominant hand. These insights are examples of how a descriptive model can inform the analysis and design of human-computer interactions.

### 7.1.5 Circumplex model of affect

The *circumplex model of affect* (CMA), presented by Russell [\[424\]](#Chp007_293-360_B9780443140969000130.xhtml#br2120) in 1980, is a two-dimensional descriptive model of human affect or emotion. The visualization positions affect in a 2D space with degrees of pleasure vs. displeasure along the horizontal axis and arousal vs. sleep along the vertical axis. See [Fig. 7.10](#Chp007_293-360_B9780443140969000130.xhtml#f0055). The term "valence" is commonly used for the pleasure-displeasure axis. One can image that at any moment each of us is positioned somewhere in the 2D space of the model.

![Figure 7.10 The circumplex model of affect (CMA) (after \[424\]).](images/B9780443140969000130/gr010.jpg)

[Figure 7.10](#Chp007_293-360_B9780443140969000130.xhtml#cf0350) The circumplex model of affect (CMA) (after [\[424\]](#Chp007_293-360_B9780443140969000130.xhtml#br2120)).

Like Guiard's model of bimanual control, the circumplex model of affect originated outside HCI, in this case in social psychology. The first use of the CMA in HCI was Schiano et al.'s [\[435\]](#Chp007_293-360_B9780443140969000130.xhtml#br2175) application of the model to the evaluation of human facial expressions, presented at the SIGCHI conference in 2000. There have been many applications since.

Griffiths et al. [\[159](#Chp007_293-360_B9780443140969000130.xhtml#br0795),[160\]](#Chp007_293-360_B9780443140969000130.xhtml#br0800) used the model to generate musical playlists. The emotional state of the user was assessed using acquired physiological and contextual data and fuzzy logic inferencing. Musical preferences were also considered. The goal was to position the user in the 2D space of the CMA. A separate process analysed music files through extracted audio features such as rhythm structure and melody features to also position songs in the CMA. Music was deemed appropriate for the playlist if the position in the CMA was close to the user position. Users were also given the option to reclassify music to a different location according to their personal sense of the music's position in the CMA.

Song and Yamada [\[462\]](#Chp007_293-360_B9780443140969000130.xhtml#br2310) used the CMA in human-robot research noting that in-situ motion and expressive lighting in a robot can convey emotions. Yoshida and Yonezawa [\[539\]](#Chp007_293-360_B9780443140969000130.xhtml#br2695) suggest, in the context of the CMA, that a robot's artificial respiratory rate and heart rate can express emotion.

An interesting extension to the CMA is converting what is mostly a qualitative assessment of valence and arousal to numeric scores. For this, Russell et al. [\[425\]](#Chp007_293-360_B9780443140969000130.xhtml#br2125) recast the CMA into a 9 × 9 "affect grid" with valence and arousal along the horizontal and vertical dimensions, respectively. Assessments involve placing a check in the grid according to the estimated position for valence and arousal of a mood, facial expression, or something else. The check location yields a 1-to-9 numeric score for valence (horizontal position) and arousal (vertical position).

A related tool is Bradley and Lang's self-assessment manikin (SAM) [\[38\]](#Chp007_293-360_B9780443140969000130.xhtml#br0190). Participants are shown sketches of manikin figures with expressions of affect. There is a set for valence ([Fig. 7.11](#Chp007_293-360_B9780443140969000130.xhtml#f0060)a) and another for arousal ([Fig. 7.11](#Chp007_293-360_B9780443140969000130.xhtml#f0060)b). Words appear representing each pole, with participants asked to select a position from 1 to 9. They might be assessing themselves, or they might be assessing some other situation, such as a music sample, a facial expression, or a robot's behaviour.

![Figure 7.11 Presentation sheet for self-assessment manikin (SAM) responses (after \[552\]). (a) Valence items. (b) Arousal items.](images/B9780443140969000130/gr011.jpg)

Figure 7.11 Presentation sheet for self-assessment manikin (SAM) responses (after [\[552\]](#Chp007_293-360_B9780443140969000130.xhtml#br2760)). (a) Valence items. (b) Arousal items.

There is an implication for models when using SAM or the affect grid to assign numeric codes for emotional states. The process shifts the CMA model from descriptive to analytic. It is not quite a predictive model, since no predictions are generated, but it is more than a "partition of a problem space," since the assessment is numeric. It becomes an analytic model.

Other uses of the circumplex model of affect in HCI include the following:

*   Conveying emotion through shape-changing interfaces [\[473\]](#Chp007_293-360_B9780443140969000130.xhtml#br2365)
