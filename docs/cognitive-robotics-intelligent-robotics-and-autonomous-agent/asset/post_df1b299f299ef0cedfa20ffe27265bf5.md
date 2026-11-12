
![](img/3dbcfad67b8516752e436bc9e574de5a_35_0.png)

**Figure 2.3** Darwin X and a hippocampal model of episodic memory. (a) The overall neural network architecture included neuronal groups for the visual “what” and “where” streams (V1 → V2/4 → IT, V1 → V2/4 → Pr, respectively), head direction system (HD), reward system (R+, R–, S), and hippocampus. (b) Subfields within the hippocampus neural group. Arrows denote synaptic projections between subgroups. (c) Schematic of a dry variant of the Morris water maze. Colors denote landmarks; numbers denote starting groups of trials. (d) Darwin X Brain-Based Device. The hidden platform was a piece of black construction paper that Darwin X could not see with its camera but could detect with a downward-facing IR sensor. Adapted with permission from Krichmar, Nitz, et al. 2005.

neurobiologically plausible neural network (Krichmar and Edelman 2002). Darwin VII autonomously explored its environment and sampled stimuli that contained positive and negative values (figure 2.4). Through its experiences, Darwin VII built up perceptual categories of the objects it sampled. Darwin VII’s simulation was based on the anatomy and physiology of vertebrate nervous systems. The simulated nervous system comprised a number of areas labeled according to the analogous cortical and subcortical brain regions for vision, auditory processing, and value. Each area contained different types of neuronal units consisting of simulated local populations of neurons or neuronal groups.

![](img/3dbcfad67b8516752e436bc9e574de5a_36_0.png)

**Figure 2.4** Darwin VII robot and neural network. (a) Darwin VII consists of a mobile base equipped with several sensors and effectors. Darwin VII is constructed on a circular platform with wheels that permit independent translational and rotational motion, with pan and tilt movement for its camera and microphones, and with object gripping by a one-degree-of-freedom manipulator or gripper. The CCD camera, two microphones on either side of the camera, and sensors embedded in the gripper that measure the surface conductivity of stimuli provide sensory input to the neural simulation. Eight infrared (IR) sensors are mounted at 45° intervals around the mobile platform. The IR sensors are responsive to the boundaries of the environment and were used to trigger reflexes for obstacle avoidance. All behavioral activity other than obstacle avoidance is triggered by signals received from the neural simulation. (b) The regional and functional neuroanatomy of Darwin VII. There are six major systems that make up the simulated nervous system: an auditory system, a visual system, a value system, a taste system, triggering behavior, a visual tracking system, and a value system. The 64 x 64 gray-level pixel image captured by the CCD camera was relayed to a retinal area R and transmitted via topographic connections to a primary visual area VA. Three subpartitions in VA were selective for blob-like features, short horizontal line segments, or short vertical line segments. Responses within VA closely followed stimulus onset and projected topographically via activity-dependent plastic connections to a secondary visual area analogous to the inferotemporal cortex (IT). The frequency and amplitude information captured by Darwin VII's microphones was relayed to a simulated cochlear area (LCoch and RCoch) and transmitted via mapped topotonic and activity-dependent plastic connections to a primary auditory area A1. A1 and IT contained local excitatory and inhibitory interactions producing firing patterns characterized by focal regions of excitation surrounded by inhibition. A1 and IT sent plastic projections to the value system S and to the motor areas M.app and M.ave. These two neuronal areas were capable of triggering two distinct behaviors, appetitive and aversive. The taste system (T.app and T.ave) consisted of two kinds of sensory units responsive to either the presence or absence of conductivity across the surface of stimulus objects as measured by sensors in Darwin VII's gripper. The taste system sent information to the motor areas (M.app and M.ave) and the value system (S). Area S projected diffusely with long-lasting, value-dependent activity to the auditory, visual, and motor behavior neurons. The visual tracking system controlled navigational movements, in particular the approach to objects identified by brightness contrast with respect to the background. To achieve tracking behavior, the retinal area R projected to area C ("colliculus"). Source: Adapted with permission from Krichmar and Edelman 2002.

The simulated nervous system contained 18 neuronal areas, 19,556 neuronal units, and approximately 450,000 synaptic connections. Figure 2.4b shows a high-level diagram of the different neural areas and the synaptic connections between neural areas in the simulated nervous system. A neuronal unit in Darwin VII was simulated with a mean firing-rate model, and the activity of such a unit corresponded roughly to the firing activity of a group of neurons averaged over a time period of 200 ms. This corresponded to the time needed to process sensory input, compute neuronal unit activities, update the connection strengths of plastic connections, and generate motor output.

The total contribution of synaptic input to unit $i$ was given by

$$A_i(t) = \sum_{j=1}^N c_{ij}s_j(t)$$

where $N$ is the number of connections to unit $i$, $c_{ij}$ is the weight value of the connection projecting to unit $i$ from unit $j$, and $s_j(t)$ is the activity of unit $j$ at time step $t$. Negative values for $c_{ij}$ corresponded to inhibitory connections. The activity level of unit $i$ was given by

$$S_i(t+1) = \phi(tanh(g_i(A_i(t) + \omega s_i(t))))$$

where

$$\phi(x) = \begin{cases} 0; x < \sigma_i \\ x; otherwise \end{cases}$$

and $\omega$ determined the persistence of unit activity from one cycle to the next, $\sigma_i$ is a unit-specific firing threshold, and $g_i$ is a scale factor, which differed depending on the neural area.

Connections within and between neuronal areas were subject to activity-dependent modification following a value-independent and a value-dependent synaptic rule. Synaptic modification was determined by both pre- and postsynaptic activity and resulted in either strengthening or weakening of the synaptic efficacy between two neuronal units. The Bienenstock, Cooper, and Munro (BCM) learning rule was used to govern synaptic change because it has a region in which weakly correlated inputs are depressed, and strongly correlated inputs are potentiated (Bienenstock, Cooper, and Munro 1982).

Value-independent synaptic changes in $c_{ij}$ were given by

$$\Delta c_{ij}(t+1) = \varepsilon(c_{ij}(0) - c_{ij}(t)) + \eta s_j(t) F(s_i(t))$$

where $s_i(t)$ and $s_j(t)$ are activities of post- and presynaptic units, respectively, $\eta$ is a fixed learning rate, $\varepsilon$ is a decay constant, and $c_{ij}(0)$ is the initial ($t=0$) weight of connection $c_{ij}$. The decay constant $\varepsilon$ governed a passive, uniform decay of synaptic weights to their original starting values. The function $F$ is a piecewise linear approximation of the BCM learning rule.

The synaptic change for value-dependent synaptic plasticity was given by

$$\Delta c_{ij}(t+1) = \varepsilon(c_{ij}(0) - c_{ij}(t)) + \eta s_j(t) F(s_i(t)) \overline{S}$$

where $\overline{S}$ is the average activity of the value system S (see figure 2.4b).

Darwin VII's environment consisted of an enclosed area with black walls and a floor covered with opaque black plastic panels, on which metallic cubes were distributed (figure 2.4a). The top surfaces of the blocks were covered with black-and-white patterns: blobs and stripes. Stripes on blocks in the gripper could be viewed in either a horizontal or vertical orientation, yielding a total of three stimulus classes of visual patterns to be discriminated (blob, horizontal, and vertical). A flashlight mounted on Darwin VII and aligned with its gripper caused the blocks, which contained a photodetector, to emit a beeping tone when Darwin VII was in the vicinity. The sides of the stimulus blocks were metallic and could be rendered either strongly conductive (“good taste,” or appetitive) or weakly conductive (“bad taste,” or aversive). Gripping of stimulus blocks activated the appropriate taste
