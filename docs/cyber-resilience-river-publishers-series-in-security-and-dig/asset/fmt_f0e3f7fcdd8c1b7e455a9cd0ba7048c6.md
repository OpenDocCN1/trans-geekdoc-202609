
### 4. Methods for analyzing the structural and functional cyber resilience of critically important information infrastructure

The document describes the methodology for analyzing the structural and functional cyber resilience of critically important information infrastructure: identification and classification of key infrastructure and technological components, determination of structural and dynamic relationships, identification of significant external and internal factors, results of predictive modeling of infrastructure operation with growing security risks, the calculation results of the cyber resilience targets.

### 5. Regulations for adaptation and implementation of `ECP`

The document contains a description of the approach to adapt `ECP` to the realities of a particular macro-region. The document describes the steps to create and implement the required business continuity process.

### 6. `ECP` implementation plan in a pilot area

The document describes the necessary steps to implement an `ECP` in a pilot area.

### 7. Instructions for implementing `ECP` in the pilot zone

The document contains a description of specific actions for company staff to ensure the required business continuity. It includes the procedure for determining key subsystems and technological processes, the calculation algorithms for cyber resilience target indicators for critically important infrastructure, `BIA` and `RA` assessment procedure using ready-made methods and examples, algorithms for updating standard threat and vulnerability catalogs, the procedure for using recommended measures to ensure business continuity, algorithms adaptation of finished `BCP/DRP`, etc.

### 8. Further action plan

The work plan for the next stage.

#### Infrastructure surveillance stage

At the stage of surveillance the business information infrastructure and data collection of key services and subsystems, the following actions are performed. At first, the general procedure for data collection is determined, the necessary working materials for interviewing and meetings (schedules, questionnaires, methods of data collection and process) are prepared. Then IT service map that provides critically important business processes is created, it contains:

*   **IT service name**
*   **Degree of IT service influence (criticality) on the company business**
    *   **High** — this service is the key to the company services package and the company income, stability and prestige are highly dependent on its operation
    *   **Medium** — this service is a demanded service, but its availability has little effect on the company business
    *   **Low** — this service is a little demanded service, its inaccessibility can pass unnoticed by the company business
*   **Determination of the functional infrastructure elements that ensure these services’ delivery**
*   **Service dependence degree assessment on this functional system element**

An example of the surveillance results of the company information infrastructure is presented in [Table 3.7](#Ch04.xhtml#cap_lbl0299).

**Table 3.7** An example of the surveillance results of the company’s information infrastructure

| No. | Material Name | Content |
| --- | --- | --- |
| 1 | Overview of the known approaches to ensure the company business continuity. Motivation for `BCM`'s own approach. | The results of a critical analysis of the known approaches to ensure the company business continuity in a particular subject area. This includes the advantages and disadvantages of known approaches, the specifics of their application and limitations, data of structuring the typical business continuity processes, the involvement of TOP management and staff in `BCM`, examples of the classification of key IT services and IT subsystems of critically important information infrastructure, examples of cyber resilience targets, methods for calculating cyber resilience indicators, `BIA` and `BCP/DRP` examples, etc. |
| 2 | Map of IT services and IT subsystems of critically important information infrastructure | List and description of IT services and IT subsystems of critically important information infrastructure, decomposition into components (computer networks and systems, communication channels, protocols and software) |
| 3 | Threat Model. Risk assessment of business interruption. | The list of the relevant threats to business continuity for this enterprise, the possible damage assessment, a list of residual risks and proposals for risk management |
| 4 | Map of key IT services and IT subsystems of critically important information infrastructure in terms of ensuring business continuity | Description of the key IT services and IT subsystems of the critically important information infrastructure, their classification and ranking in terms of ensuring business continuity. |
| 5 | Map of the company's critically important business processes Карта критически важных бизнес-процессов компании | Description of the company's critically important business processes based on a certain model, such as `eTOM` |
| 6 | The Report analyzes the level of maturity of the `BCM` program company | The report contains an analysis of the maturity level of the existing business continuity process in the company. This includes assessments of the completeness of recovery plans and the matrix of responsibilities, assessments of the adequacy of organizational and technical measures of `BCM`, completeness of existing policies and standards of BCM, regulations and procedures for personnel management in emergency situations, etc. |
| 7 | Business requirements for the structurally-functional cyber resilience critically important information infrastructure | Business metrics and measures to ensure the required business continuity. |
| 8 | Suggestions for refinement of the terms of reference for the development and implementation of `ECP` Program | Requirements for an enterprise business continuity program, `ECP`. Including cyber resilience requirements for key IT services and IT subsystems of critically important information infrastructure |
| 9 | Further action plan | The list of activities for the support and maintenance of `ECP` program, planned dates, expected results, responsibilities. |

#### Detection dependencies between infrastructure components

Detection dependencies between key components of a company’s information infrastructure involves determining the potential threats and vulnerabilities, and then, for example, using a `scenario approach`, determining the business interruption risks. An example of detection dependencies between key IT services and IT subsystems of a company information infrastructure is shown in [Table 3.8](#Ch04.xhtml#cap_lbl0300).

An example of the resilience assessment of the key components of the critically important information infrastructure is shown in [Table 3.9](#Ch04.xhtml#cap_lbl0301).

**Table 3.8** Dependencies between key infrastructure components

| | Criticality | BTS | BSC | MSC/VLR | HLR/AC | PrePaid Platform | OAM&P | AIS |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Landline | High | Medium | High | High | High | High | Low | |
| Landline between a mobile subscriber and a PSTN or another local mobile operator | High | Medium | High | High | High | High | Low | |
