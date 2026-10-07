
## E.P. Yakovachev / Cyber Resiliency Measurements and Metrics

Of the standard selected, the NIST standard will offer an approach to cybersecurity controls at the US Federal levels. This NIST standard offers both management practices and practical controls, also known as requirements to meet the cybersecurity integrity goals. Selection of NIST was the objective of Step #1 is Cybersecurity. It offers both management and technical guidelines, thus measures organization goals and practices, while technical controls, or requirements to create and meet the overall goals. NIST offers quantifiable values to be used within a metrics discussion. NIST also offers a metric and known practical guidance to industries for, thus trusted and known sources of information. Selecting with these values ensures known and agreed upon data will be used in the metrics generation and any outcomes will be trusted through those affiliations. They may also be reused and shared with other organizations using the same standards.

Step #4 is the most complicated as the lower level indicator represents that guideline and meets the objectives of the data selected in steps #1, #2, and #3. As of today, there are hundreds of control examples in the NIST standard selected, so the hard part is picking a relevant controls meeting the needs and description of ‘resilient’, ‘cybersecurity’. The results from the first 3 steps are shown below a refresh to assist with this step:

| Description |
|---|---|
| NIST Item: | GOAL: ‘Resilience in Cybersecurity’ |
| Definition: | The ability to adapt changing conditions and prepare for, withstand, and rapidly recover from disruption |
| 4 R Title Objective | Description | Apply (Y/N) | Why |
|---|---|---|--|
| Robustness | ability to maintain critical operations and functions | Y | Stated in 4 objective |
| Resourcefulness | ability to skillfully perform, respond to and manage a crisis or disruption | Y | Similar words to the 4R objective |
| Rapid recovery | ability to turn and/or reconstruct normal operations as quickly and efficiently | Y | Similar words to the 4R objective |
| Redundancy | there are back-up resources | N | N/A |
| Standard US—NIST 800-53 | Provides Security and Privacy Controls for US Federal Information Systems and Organizations |

In the next phase a single control will be selected from the NIST standard and a description applied in table 5 below:

**Table 5. High Level Standard**

| Standard Technique | Control and Description | Text | Selection Criteria |
|---|---|---|---|
| NIST SP 800-53 Rev 4 | CP-10 - Information System Recovery and Reconstitution | The organization provides for the recovery and reconstitution of the information system to a known state after a disruption, compromise, or failure. | This control was selected as an easy fit to the resilient discussion and a common sense control that aligns to resiliency. |

At this phase of the selection process, all the data is gathered and summarized in plain read terms as shown in Table 6 below:

**Table 6. Final Metric Wording**

(Broken down)
Resilience in Cyberspace objective is to measure the ability to adapt to changing conditions and prepare for, withstand, and rapidly recover from disruption by tracking NIST SP 800-53 control ‘CP10’, titled Information System Recovery and Reconstitution [to a known state after a disruption, compromise, or failure] to provide a resilient metric as a common measurement to track of Robustness, Resourcefulness, and Rapid recovery of the ICT system.

(combined sentence)
Resilience in Cyberspace objective is to measure the ability to adapt to changing conditions and prepare for, withstand, and rapidly recover from disruption by tracking NIST SP 800-53 ‘CP10’, titled Information System Recovery and Reconstitution [to a known state after a disruption, compromise, or failure] to provide a resilient metric as a common measurement to track of Robustness, Resourcefulness, and Rapid recovery of the ICT system.

With the common metric defined in easy terms in the Table 6 above, the focus will now be on creating the values to quantify and visually represent the data. The data within the brackets in Table 6 states what the metric will be measured:

“To a known state after a disruption, compromise, or failure”

Since returning of an ICT system to a known state is a very vague term the following provides a high level example to complete the process. For the example, the ICT systems will have 10 servers and 100 operational workstations. The known state of the system is 10 servers 99% of the time and 100 workstations 99% of the time. The term is operated with the workstations as they are in use when they are working and not necessarily needed 24 X7, while the servers are needed 24 x7 minus any maintenance periods, thus the known state is:

+ - 10 Servers online 99%
- 100 Workstations online 99% of the time when needed by users

Disruption, compromise, or failure can be defined as anything less than the values identified above and a total of three metrics can be created from this example:

+ - Servers Operational,
- Workstation Operational, and
- Combined Devices.

The values presented are now applied to graphic:

![](img/fe2b494937620764de04f8bcd27e5e_328.png)

Figure 3. Resilient Graphic

Figure 3 reflects an easy to understand example how to measure and map resiliency in a graphical format, but there are more detailed needed

## E.P. Yakabowicz / Cyber Resiliency Measurements and Metrics 3.

Copyright © 2020 © IOS Press, Incorporated. All rights reserved.
Cybersecurity in the Arctic, edited by B. D. Trump, et al. IOS Press, Incorporated, 2020. ProQuest Ebook Center.
http://ebook.proquest.com/libq/detail.action?docID=6359588.
Created by cm 2023-01-23 12:32:27.

![](img/fe2b494937620764de04f8bcd27e5e_329.png)

Figure 4. Graphic Example

+ - Inp’ is the initial performance: 10 Servers
- ‘Tip’ is the time to restore the initial performance, or final performance if the time is 10 minutes
- ‘Tfp’ is the time to reach the final performance: 15
- ‘imp’ is the impact of the threat measured by the decrease of performance (measure risk): 2
- ‘Imx’ is the lowest performance value: 2
- ‘Ap2’ does as there is the negative difference between the final and the initial performance (underperforming), 1
- ‘Enp’ is the end of the performance value: 9
- ‘Time’ is the overall period of the measurement: 20.

When applying the quantifiable data presented above and mapped back to the overall metric statement, the following occurs:

| Resilience in Cyberspace objective is to measure the ability to adapt to changing conditions and prepare for, withstand, and rapidly recover from disruption by tracking NIST SP 800-53 control ‘CP10’, titled Information System Recovery and Reconstitution [to a known state after a disruption, compromise, or failure] to provide a resilient metric as a common measurement to track of Robustness, Resourcefulness, and Rapid recovery of metric has shown initial performance of 10 servers (initial performance) reduced to 9 servers (end performance) after that disruption lasted 20 minutes (time). Recovery time of the 9 servers started after 10 minutes (Tip) and finished at 15 minutes (TIp). Of the 10 servers impacted, 2 (Imx) where not impacted at all or with little disruption |
