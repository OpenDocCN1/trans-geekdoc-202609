
# E.P. Yakabowicz / Cyber Resiliency Measurements and Metrics 311

after recovery on the right. It also represents metric objectives discussed of being easy to understand, repeatable, and reflect relevant indicators. The graphic is also not over complex, meaningful, and reflects value to the organization.

![](img/fe2b494937620764cde04f8bcd27e5e0_322_0.png)

Figure 1. Resilient Graphic

Resilience is measured over time with performance values in Figure 1 with the following attributes:

- 'Inp' is the initial performance,
- 'P' is the rate of change, or performance,
- 'Tip' is the time to restore the initial performance, or final performance if not the same,
- 'Tfp' is the time to reach the final performance,
- 'imp' is the impact of the threat measured by the decrease of performance (measure risk),
- 'Imx' is the lowest performance value,
- Ap is broken into:
    * Positive difference between the final and the initial performance (performing),
    - Negative difference between the final and the initial performance (underperforming), or,
    - No change where Inp Enp equals,
- 'Enp' is the End of performance value, and
- 'Time' is the overall time period of measurement.

#### E.P. Yakabowicz / Cyber Resiliency Measurements and Metrics 312

Another version of this resilient graphic shown in Figure 2. It reflects some potential rates of change in the measure of resilience or the possible outcomes of the event. The graphic only captures the resilient nature of the measurement in either positive, no, or negative, which is a simple view of resiliency. Each line starts at normal operations at initial performance on the left axis, continues through the disruption in the middle and finishes as the same or different normal operations level on the right. To note the measurement is 1 over time, 2 starts at one operational known defined as normal or initial performance and 3 may finish at the same operational level (blue) or different with worse below (red) the initial performance or better above (green).

![](img/fe2b494937620764cde04f8bcd27e5e0_323_0.png)

Figure 2. Possible Outcomes

These graphics are useful in the following section to explain the end to end process in the creation of a metric to reflect an easy to understand visual aid for resiliency. It also reflects the important aspects of measuring resilience within all the input variables. As a good standard, this visual representation provides the very basic goals and value in the use of metrics by reflecting an easy to understand graph to represent the resilient nature of an item and how to track both positive and negative resiliency to an event. Reflecting positive and negative results represent value to the business managers, who have investments produced something of value to the organization that is resilient to disruption. The next section will walk through some basic and generic steps of creating a resilient metric.

# 5. Creating a Resilient Metric

The goal of this is to address some generic steps to create an easy to understand, repeatable, and relevant measurement for a resiliency metric using the data presented. This section will leverage the workload addressed to point to form the knowledge

Copyright © 2020. IOS Press, Incorporated. All rights reserved.
Cybersecurity and Resilience in the Arctic, edited by B. D. Trump, et al., IOS Press, Incorporated, 2020. ProQuest Ebook Central,
://ebookcentral.proquest.com/libqi/detail.action?id=6359988.
Created from i on 2023-03-12 12:32:27.

#### E.P. Yakabowicz / Cyber Resilience Measurements and Metrics 313

necessary to create a resilient metric that is easy to understand. The following ‘5 step resiliency metric process’ will include:

- Select a sector/industry from the NIST critical infrastructure list and obtain a definition of an sector;
- Review the 4R’s that will assist with characterization and goals (or intent) of the metric;
- Select an industry or regulatory guideline typically used by an organization, and;
- Select a lower level indicator that represents guideline and meets the objectives of steps #1 and #2 (to be explained below).
- Create the resiliency graph.

This example will be simple and easy to understand method to create a metric. Potentially, this example may or not apply to other industries and may be more difficult based on the actual resilient goals and objectives of an organization. This is to serve as an example and method to help and understand the basic concepts within some practical buildings of building a resilient metric.

Step #1 consists of selecting a industry from the NIST critical infrastructure list. It serves as a good starting point in providing the proper language to quantify each of the sectors have been agreed upon within the US Government space. If the NIST list does not work for reader, try to obtain one that provides the information that will quantify the highest level objectives. For this example the following is used for this example:

- NIST Item: ‘Resilience in Cyberspace’
- Definition: The ability to adapt to changing conditions and prepare for withstand, and rapidly recover from disruption.

Table 1. Step 1 Select With Definition

| Description | Content |
|---|---|
| NIST Item: | ‘Resilience in Cyberspace’ |
| Definition: | The ability to adapt to changing conditions and prepare for, withstand, and rapidly recover from disruption |

Now draw down the definition into quantifiable attributes as to express, measure, or define the problem and solution in easy terms that apply to the sector. In this example:

- measuring the ability of systems to
- adapt to changing conditions of
- Cyberspace
- to prepare for, withstand, and rapidly recover from disruption.

Step #2 is to review the Berkeley and Wallace [33] NIAC 4R’s of Robustness, Resourcefulness, Rapid recovery, and Redundancy and the attributes that align to the resiliency goals of the organization (P. 16). This doing step provides a foundation for further establishing wording and language beyond the NIST data to address the purpose of

Copyright © 2020 IOS Press, Incorporated. All rights reserved.
Cybersecurity and Resilience in the Arctic, edited by B. D. Trump, at IOS Press, Incorporated, 2020. ProQuest Ebook Central, http://ebook.proquest.com/libqui/detail.action?docID=6359888.
Created from cmu 2023-01-23 12:32:27.

#### the metric and provide business 'resilient' terms to assist in writing of the metric. The example below will build off Step #1 and build out 4R's, if they apply:

- NIST Item: 'Resilience in Cyberspace'
- Objective: The ability to adapt to changing conditions and prepare for, withstand, and rapid recovery from disruption
- 4 R's: As shown in table 2, place the 4R's on the left, description, and then yes or no column, with a final column to explain why the choices were made. All words should be kept to a minimum using words that quantify as 'ability to', 'prepared for', 'there are':

# Table 2 4R Table

| 4R Title | Description | Apply (Y/N) | Why |
|---|---|---|---|
| Robustness | ability to maintain critical operations and functions | | Stated in 4R objective |
| Resourcefulness | ability to skillfully prepare for, respond to and manage a crisis or disruption | Y | Similar words to the 4R |
| Rapid recovery | ability to return and/or reconstruct normal operations as quickly as efficiently | Y | Similar words to the 4 objective |
| Redundancy | there are back-resources | N | N/A |

Based on selections in table 2, the first 3 apply (Robustness, Resourcefulness, and Rapid recovery) and the 4th does not (Redundancy). Methods may vary with other metrics creation. These results should be stored for later use in the metric generation process.

Step #3 is the process to select a well-known industry, technology, regulatory standard that is mature and contains a framework or controls that can be leveraged to create the metric. In this example, the following will be shown as in table 3:

Table 3. Select industry, technology, or regulatory standard

| Standard | Description |
|---|---|
| US – NIST SP 800-53 | Provides Security and Privacy Controls for US Federal Information Systems and Organizations |

The reader should take note with this example that many cybersecurity standards similar to those selected in table 3 above are focused on 'risk' rather than 'resiliency'. Although risk and resilience are linked in providing different layers of protection and reporting standards, this paper will focus on resilience and some practices to understand and create resiliency metrics. The comparing and contrasting risk to resiliency will not be addressed in this paper, but note there are research papers on within the resilient and resiliency topic of discussion.
