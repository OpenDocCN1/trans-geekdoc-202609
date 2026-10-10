
At a stripped-down level, interaction involves humans using their sensors and responders to monitor and control devices, machines, or systems that include computing technology. We saw a typical human factors view of this in Chapter [2](#Chp002_31-91_B9780443140969000087.xhtml) (see [Fig. 2.2](#Chp002_31-91_B9780443140969000087.xhtml), p. 34). The internal states of the human and machine interact in a closed-loop system through controls and displays (the machine side) and motor-sensory behaviours (the human side). By convention, the terms "input" and "output" are with respect to the machine. So, inputs, or input devices, are inputs to the machine that are controlled or manipulated by human outputs. Most commonly, human outputs are limbs – the fingers, hands, arms, legs, feet – but speech, articulated sounds, eye motions, blinks, winks, head nods, breath, brain signals, and so on, can also serve as human outputs. Some of these communication channels are extremely important for users with special needs, for example.

There is a long history of human factors research following a classical "knobs and dials" view [\[73](#Chp003_93-160_B9780443140969000099.xhtml#br0365),[495\]](#Chp003_93-160_B9780443140969000099.xhtml#br2475). Using responders, the human operator manipulates knobs (controls), perhaps with a goal in mind, while engaging senses to perceive the status of a system on dials (displays).^([^(45)](#fn45))

We begin with the basic interactions between humans and computers (the knobs or controls). With the arrival of the graphical user interface in the 1980s, the most common interactions involve pointing and selecting, perhaps with a mouse. Setups are more varied today with the proliferation of smartphones and tablets, and environments such as gaming, virtual reality, eye tracking, and even brain-computer interfaces (BCI).

## 3.1 Techniques

Many interactions on computer systems exhibit a pattern of "forming an intent" followed by "confirming an intent." These expressions nicely map into the more common yet narrower terms "pointing" (forming an intent) and "selecting" (confirming an intent). Indeed, throughout the history of HCI, devising novel point-select methods and evaluating them in user studies is a common research theme. This research flourished after the introduction of the graphical user interface (GUI) and the computer mouse in the early 1980s, as detailed in Chapter [1](#Chp001_1-29_B9780443140969000075.xhtml).^([^(46)](#fn46))

The possibilities for point-select operations are vast. [Fig. 3.1](#Chp003_93-160_B9780443140969000099.xhtml#f0010) provides a coarse summary while opening the door for deeper examination. In the table, an SOI is a "selectable object of interest," such as a button, icon, or other target of interest.

![Figure 3.1 Example methods for pointing and selecting. Note: SOI = selectable object of interest.](images/B9780443140969000099/gr001.jpg)

Figure 3.1 Example methods for pointing and selecting. Note: SOI = selectable object of interest.

The most common point-select methods fall within the first three rows of [Fig. 3.1](#Chp003_93-160_B9780443140969000099.xhtml#f0010). Other methods are included to acknowledge the breadth of possibilities.

It is worth noting that form-confirm (FC) actions exist in a hierarchy. At a high-level, an FC action might be a task such as booking a hotel online. This involves considering alternative hotels (forming an intent) and then narrowing in on or choosing a hotel to book (confirming an intent). The task contains lower-level FC operations, such as viewing and confirming rooms options (e.g., "breakfast included"), entering email or phone contact information, or entering a credit card number. And each button that is clicked or character that is entered requires an even lower-level FC action, such as positioning a finger on a key, then pressing the key. This multi-level view of FC actions potentially maps into Newell's time scale of human action presented in Chapter [2](#Chp002_31-91_B9780443140969000087.xhtml) (p. 33).

The most common evaluation techniques for point-selection operations follow a Fitts' law paradigm, which we present in Chapter [7](#Chp007_293-360_B9780443140969000130.xhtml).

### 3.1.1 Pointing

The archetype device for pointing is the computer mouse. Pointing involves manoeuvring the device to control the position of a pointer or tracking symbol (e.g., ![Image](images/B9780443140969000099/fx001.jpg), ![Image](images/B9780443140969000099/fx002.jpg), ![Image](images/B9780443140969000099/fx003.jpg)) on a display. The interaction is "indirect" because a tracking symbol is required as an intermediary, connecting the device movement or position to the selectable object of interest.

Besides the mouse, there are other indirect pointing devices and these often use different methods for pointing and selecting. As a general rule, if a cursor or pointer is involved, the interaction is indirect. Laptop computers typically include a touchpad, also an indirect pointing device. The touchpad is built-in: Pointing occurs by moving a finger on the touchpad surface.

For all indirect pointing techniques, it is important to consider the relationship between interaction with the input device – the control – and movement of the on-screen tracking symbol – the display. Such control-display relationships are presented in greater detail later in this chapter.

For direct pointing, there is no need for a tracking symbol or cursor. The most obvious example is finger input on touchscreen devices such as tablets or smartphones. Another example is eye tracking input where the eye looks directly at an object and it is selected, typically using dwell-time selection.

### 3.1.2 Selecting

Selection typically occurs by pressing and releasing a button on or near a device, such as a mouse, touchpad, or game controller. For touchpads, there are at least three selection methods: (i) press a button situated near the touchpad, (ii) lift the finger from the touchpad and quickly tap on the surface, or (iii) keep the finger intact on the surface while pressing firmly down. The emergence of the latter technique is chronicled in Chapter [7](#Chp007_293-360_B9780443140969000130.xhtml) (see [Fig. 7.14](#Chp007_293-360_B9780443140969000130.xhtml), p. 307).

If a button is not available, dwell-time selection is possible. The user acquires an object for a pre-determined time interval whereupon selection occurs. In this case, feedback is needed to inform the user of the dwell progress. See [Fig. 3.2](#Chp003_93-160_B9780443140969000099.xhtml#f0015).

![Figure 3.2 Dwell-time selection feedback.](images/B9780443140969000099/gr002.jpg)

Figure 3.2 Dwell-time selection feedback.

### 3.1.3 Point-select improvements

Many ideas have been proposed and evaluated for improving the point-select experience. These often involve changing properties of the interaction in real time, during the pointing or selecting actions. The goal is to make point-select operations faster or more accurate.

#### 3.1.3.1 Spatial hysteresis

One possibility to improve selection is *spatial hysteresis*. Using spatial hysteresis, a larger virtual target is added around a target. The mouse pointer is deemed to enter the target when it enters the "real target." The pointer leaves the target when it exits the hysteresis zone. Thus, a target can be selected if the pointer enters the target, then leaves the target but remains in the hysteresis zone. See [Fig. 3.3](#Chp003_93-160_B9780443140969000099.xhtml#f0020).

![Figure 3.3 Spatial hysteresis. On the right, spatial hysteresis is used. The target is selected since the pointer enters the target, then leaves the target but remains in the spatial hysteresis zone. Note: The dashed line showing the spatial hysteresis zone does not appear on the display.](images/B9780443140969000099/gr003.jpg)
