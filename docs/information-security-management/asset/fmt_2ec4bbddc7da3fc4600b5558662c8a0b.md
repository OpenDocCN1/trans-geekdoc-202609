
| Six Sigma || Consists of techniques and tools to measure and implement processes and process and quality improvements. It is fundamentally prescriptive in outlining what must be done and how to do it. |

| CMM / CMMI || The Capability Maturity Model (CMM) consists of a set of criteria that define the maturity of organizational processes. It is primarily descriptive rather than prescriptive. CMMI builds on CMM to include integration criteria. Specialized organizations such as the CMMI Institute® provide cybersecurity-specific CMMI criteria, training, and auditing. |

Tactics are generally the steps taken to achieve a strategy. Using the chess analogy, a strategy might be to use the king’s bishop to control two diagonals where it can attack the central square, or to use a pawn to open up pathways for the pieces to advance from the back and into the fight for the central squares. Tactics are the moves according to the rules, such as a piece that can move horizontally, or a tactic might be to move the bishop to an active square. Technology operations incorporates both the strategy and the tactics to ensure that systems security and functionality are sustained ([Figure 5.4](#9781284211658_CH05_01.xhtml#c5-fig0004)).

![FIGURE 5-4 Strategy, Tactics, and Operations ¶ © Domin_domin/E+/Getty Images.](images/9781284236378_CH05_FIGF04.jpg)

FIGURE 5-4 Strategy, Tactics, and Operations ¶ © Domin_domin/E+/Getty Images.

Organizations have primary activities and support activities. Primary activities include inbound logistics (inputs), operations (processing), outbound logistics (distribution), marketing and sales, and service. This is sometimes referred to as the value chain. Support activities are those that facilitate the primary business activities. For instance, a hospital’s main function is to treat patients, but the health information systems are necessary to support that function. Thus, primary activities are supported by the technological infrastructure. Defining the technology strategy encompasses the business and security processes across the value chain. The functions of business and security are mutually supportive. Security is useless if systems are not operational, indeed, a class of attacks that include denial of service specifically aim at disrupting business. Likewise, a business cannot function effectively without good security. The idea behind defining the technology strategy holistically as part of ISML is because of these mutually supportive and interdependent functions.

One method for formulating strategy is to utilize a principles framework. Principles guide the strategy, which determine the tactics. There are many ways to categorize principles, but three of the most common are management principles, vendor principles, and system principles ([Figure 5.5](#9781284211658_CH05_01.xhtml#c5-fig0005)). Management principles include the degree of risk the leadership in the organization is willing to accept, for example, deciding to delay security patching to maintain productivity would reflect a high risk-taking management approach. The importance of time to market compared to developing quality and rich features in a product has a bearing on the effort put into testing and security processes. Whether management is focused on cost savings to deliver low-cost goods or services compared to producing or delivering something unique may determine decisions such as the extent to which cybersecurity is baked into their cost of doing business.

![FIGURE 5-5 Principles Framework](images/9781284236378_CH05_FIGF05.jpg)

FIGURE 5-5 Principles Framework

Vendor principles include whether to leverage a single vendor or acquire technologies that are the best in their categories even though it may involve many vendors. Similarly, a company may try to leverage technologies that are feature rich with good technical support that tend to be proprietary, versus selecting open-source technologies that may require substantial inhouse development and support. Vendor principles also include whether or not to work with small emergent vendors who may be more innovative than larger, more established vendors, but may carry greater risk, or pick one that has been in business for a long time. They also include whether to build the technologies, or buy them commercially off-the-shelf (COTS).

System principles include whether to design systems around processes or the data, whether to produce centralized or distributed solutions, whether to build or buy a technology that is general purpose and uniform, or whether it should be highly customized or customizable. Finally, a system principle would include whether the solution fits horizontally across an organization and its value chain, or whether it serves a particular vertical, such as a department or business function. Here, the concept of cloud native is important. Cloud native is a term used to describe container-based environments, which can be migrated easily between on-premise systems and the cloud.

To determine the working principles for our technology selections, a survey may be distributed to the stakeholders. The survey would use a Likert scale of, say, 1 to 7 points, with competing principles arranged on polar ends of the survey, such as to the question: “Should we leverage proprietary vendor solutions for volume discounts and feature richness” on pole 1, and “Should we leverage open-source technologies to keep from being locked into a vendor” on pole 7, such as seen in [Figure 5.6](#9781284211658_CH05_01.xhtml#c5-fig0006).

![FIGURE 5-6 Sample Survey Question Format](images/9781284236378_CH05_FIGF06.jpg)

FIGURE 5-6 Sample Survey Question Format

After we collect the surveys and analyze them, we start with the mean score from all the stakeholder responses, which indicates the average on where stakeholders lean on that particular principle. For example, a mean score of 6 on the question of whether to build (= 1) or buy (= 7) indicates the stakeholders strongly lean toward buying the technology. When we evaluate a technology, we should weight purchasing greater than building. Hence, given two equally appealing technology proposals, one proposed to build in-house, the other to acquire, we would lean heavily toward purchasing, but if we are the decision-maker, we might still choose to build it, but we had best be prepared to justify the decision. The standard deviation tells us how much the stakeholders agree or disagree. If there is a large standard deviation, we will want to get the stakeholders together to discuss it and iron out the principle to gain better consensus ([Figure 5.7](#9781284211658_CH05_01.xhtml#c5-fig0007)).

![FIGURE 5-7 Principles Survey](images/9781284236378_CH05_FIGF07.jpg)

FIGURE 5-7 Principles Survey

### 5.1.2 ISML and Governance Frameworks

Once the information strategy has been defined, ISML incorporates requirements from applicable governance frameworks. There are many regulations and governance frameworks that we will cover in greater detail later; for now, we’ll just discuss a few examples. Ultimately, regulatory and governance requirements end up as implementable tasks during the DevSecOps process and are used by both the Operations and Compliance departments for conformance testing and auditing.
