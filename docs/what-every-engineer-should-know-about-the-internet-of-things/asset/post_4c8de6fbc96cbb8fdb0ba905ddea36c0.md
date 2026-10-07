
Networks of 'Things'

- 8. Security concerns for weights are related to possible tampering of the weights.
- 9. The appropriateness (or correctness) of the weights is crucial for the purpose of a NotT.

A simple aggregator may implement the summation

```
$$\sum_{i=1} d_i$$
```

divided by x,
where
x is the number of data points, and where the weight for each data point is uniform.

## 2.3.3 PRIMITIVE #3: COMMUNICATION CHANNEL

A communication channel is a medium by which data is transmitted (e.g., physical via Universal Serial Bus (USB), wireless, wired, verbal). Basic properties, assumptions, recommendations, and general statements about communication channel include the following:

1. 1. Communication channels move between computing, sensing, and actuation.
2. Since data is the "blood" of a NotT, communication channels are the "veins" and "arteries", as data moves to and from intermediate events at different snapshots in time. We talk about the role of snapshots in time in Section 2.3.
3. Communication channels will have a physical or virtual aspect to them, or both. Protocols and associated implementations provide a virtual dimension. We provide a physical dimension.
4. Communication channel dataflow may be unidirectional or bidirectional. There are many conditions where an aggregator might query more advanced sensors, or potentially recalibrate them in some way (e.g., request more observations per time interval).
5. No standardized communication channel protocol is assumed; a specific NotT may have multiple communication protocols between different entities.
6. Communication channels may be wireless.
7. Communication channels may be an offering (service or product) from third-party vendors.
8. Communication channel trustworthiness may make sensors appear to be failing when the communication channel is failing.
9. Communication channels can experience disturbances, delays, and interruptions.
10. Redundancy can improve communication channel reliability. There may be more than one distinct communication channel between a computing primitive and a sensing primitive.
11. 11. Performance and availability of communication channels will greatly impact any IoT that has time-to-decision requirements (see the decision trigger primitive in Section 2.5).
12. Security and reliability are concerns for communication channels.

In Figure 2.1, 15 sensors are shown – the blue sensors indicate that these two sensors are 'somehow' failing and at specific times, i.e., they are not satisfying their purpose and expectations. As mentioned earlier, there could be a variety of sensor failure modes, some temporal and some related to data. Further, the temporal failure modes for sensors may actually be a result of the transport that data failing and not the sensors themselves. Consider also that the two failing sensors in Figure 2.1 should probably be assigned lower weights. Figure 2.1 also shows the 15 sensors clustered into three clusters with five unique sensors assigned to each. Figure 2.1 shows the data coming out each of the three clusters being input to three corresponding aggregators. It is now the responsibility of the three aggregators to turn those 15 sensor inputs into three intermediate data points.

For example, in Figure 2.1, aggregator $A_1$ might be determining how busy restaurant X is. Independent sensors in $C_1$ could be taking pictures from inside and outside (parking lot) of X, room temperature in the kitchen, motion detectors from the dining area, sound and volume sensors, light detectors, etc. So while the sensors are certainly not homogeneous, their data is processed to make a new piece of data to address one question with possible results such as the restaurant busy, not busy, and closed. And aggregators $A_2$ and $A_3$, might be doing the same for restaurants $Y$ and $Z$, respectively. Consider also not that an aggregator can be associated with different clusters.

![](img/41fdf2aa71adfa568d36836737f447e6_34_0.png)

FIGURE 2.1 The first three primitives.

## 2.3.4 PRIMITIVE #4: eUtility (EXTERNAL UTILITY)

An eUtility (external utility) is a software or hardware product or service. The current definition of eUtility is deliberately broad, to allow for unforeseen future services and products that will be incorporated in future types of NoTs yet to be defined. (Breaking this primitive down into primitives is future work.) Basic properties, assumptions, recommendations, and general statements about eUtility include the following:

1. 1. eUtilities execute processes or feed data into the overall workflow of NotT.
2. eUtilities could be acquired off the shelf from third parties.
3. eUtilities may include databases, mobile devices, miscellaneous software and hardware systems, clouds, computers, and CPUs. The eUtility primitive can be subdivided and probably should be decomposed to this model less abstract.
4. eUtilities, such as clouds, provide computing power that aggregators may not have.
5. A human may be viewed as an eUtility. A human is sometimes considered as 'thing' in public discourse related to IoT.
6. Data supplied by eUtility may be weighted.
7. An eUtility may be counterfeit; this is mentioned in element Device_ID (see Section 2.3).
8. Nonhuman eUtilities may have Device_IDs; Device_IDs may be crucial for identification and authentication.
9. Security and reliability are concerns for all eUtilities.

Figure 2 illustrates using two cloudUtilities to execute five aggregator implementations. (Note that there is no suggestion that aggregators must execute on cloud platforms – aggregators can execute on any computing platform.) Figure 2.2 shows the addition of one noncloud eUtility, eU_ (a laptop).

## 2.3.5 PRIMITIVE #5: DECISION TRIGGER

A decision trigger creates the final result(s) needed to satisfy the purpose, specification, and requirements of a specific NoT. Basic properties, assumptions, recommendations, and general statements about decision trigger include the following:

1. 1. A decision trigger is a conditional expression that triggers an action. A decision trigger's outputs can control actuators and transactions (see Figures 2.3 and 2.4). Decision triggers abstract define the end of a NotT.
2. A NoT may or may not control an actuator (via a decision trigger).
3. A decision may have a binary output, but there will also be situations where the output of a decision trigger is a nondiscrete output, i.e., a continuum of output values.

> 4 Standards Developing Organizations (SDOs) have effects as cyber-entities [IEEE, p. 2413, "Standard for an Architectural for the Internet of Things (IoT) and digital entities [JTC21 WG10 ISO/IEC 34010, "Internet of Things"] in their draft documents as of this writing.

![](img/41fdf2aa71adfa568d36836737f447e6_35_0.png)

FIGURE 2.1 The first three primitives.

![](img/41fdf2aa71adfa568d36836737f447e6_36_0.png)

FIGURE 2.2 eUtility.

![](img/41fdf2aa71adfa568d36836737f447e6_36_1.png)

FIGURE 2.3 Decision trigger.

- 4. A decision trigger may have a built-in adaption capability as the environment element (see Section 2.3) changes.
- 5. A decision trigger will likely have a corresponding virtual implementation, i.e., code.
- 6. A decision trigger may have a unique owner.
- 7. Decision triggers may be acquired off the shelf or homegrown.
- 8. Decision triggers are executed at specific times or may execute continuously as new data becomes available.
- 9. Decision trigger results may be predictions.
- 10. Analytics could be implemented within triggers; however, analytics could also be implemented within aggregators (that are executed by Utilities).
- 11. If a decision trigger feeds data signals into an actuator, then the actuator may be considered as an eUtility if the actuator feeds back into the NotT. Also, an actuator can and should be a component of the environment element (see Section 3). This model treats actuators as “consumers” of the outputs from decision triggers. But not all things are primitives in this model.
- 12. A decision trigger may feed its output back into the NotT creating a feedback loop⁵ (see Figure 2.4).

![](img/41fdf2aa71adfa568d36836737f447e6_37_0.png)

FIGURE 2.4 Decision trigger with feedback.

> ⁵ There are other feedforward mechanisms in process control theory and implementation that are outside the immediate scope of this model.
