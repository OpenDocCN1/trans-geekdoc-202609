
It's best that the thresholds are first set and run at a prescribed time to find out what the triggers need to be for this purpose. This needs to be an iterative process as the bars, or levels, for each of these can require adjustment. Once it is determined that the thresholds are correct, then the triggers need to be placed in this “learning” mode to monitor their effectiveness. Lastly, the program documentation will list a periodic review date (at least annually) for the thresholds and triggers to assess their effectiveness and potential need for change based upon this analysis.

Next, the team needs to decide how to weight each data feed. Data from an on‐site physical assessment is given a heavier weight than remote ones. Data from the internal systems of record are also given a heftier score than data coming from external feeds. This math must be clear and explainable to the audience. KC's math was published on an internal website, and a link was made available on all dashboards that took the user to that website. This openness led to acceptance of these reports with very little need to convince vendors of their value.

## A Mature to Predictive Approach

The data is now in the systems of record, in a format that is available for reporting. In addition, your team has established levels and thresholds. The intended outcome is take all this data, place it in a business intelligence or analytics tool, and go from reactive to a more predictive risk‐based approach on engaging vendors. In order to best demonstrate how it will work, let's use KC Enterprises and some of their use cases to illustrate how to move into this predictive model for Cybersecurity Third‐Party Risk.

## The Predictive Approach at KC Enterprises

All the work accomplished at KC produces the data and ability to provide analytical output for how they can manage their third‐party pool in a more deliberate rather than reactive way. The team begins by exploring and cataloging where the relevant data is stored across the enterprise. An overwhelming majority of data is found in the Third‐Party Risk Management software, yet some is also located in the purchasing software, threat intelligence systems, and the cybersecurity team's own software and tools used to manage vendor risk and their Cybersecurity Third‐Party Risk program.

Thresholds are set based upon the vendor's assigned risk category, which are consistent with the risk‐based approach that the program takes and enables for clear explanation of the “how” and “why” each vendor receives an escalation or intervention based upon the data and business intelligence software. A decision is made to use a “stoplight approach” for identifying triggers for action of red, yellow, and green to match the three levels of risk: high, medium, and low. It's also an easy way to clearly identify those that require attention (red), those that need some investigation (yellow), and vendors that are based upon the data available who present no new increased risk (green). See [Figure 15.2](#c15.xhtml#c15-fig-0002). The triggers for each level are broken down as follows:

*   **Red:** Vendors with red lights (i.e., who are high risk) are those who meet the following thresholds: 
    *   A breach within the last year
    *   A high‐Risk Acceptance that is still open
    *   A high‐risk finding that is not physically validated as remediated
    *   A trigger from `CM` that is risk‐rated as High
*   **Yellow:** Vendors with yellow lights (i.e., who are medium risk) are those who meet the following thresholds: 
    *   A breach within the last two years
    *   A medium‐ or low‐Risk Acceptance that is still open
    *   A medium‐ or low‐risk finding that is not physically validated as remediated
    *   A trigger from `CM` that is risk‐rated as Medium
*   **Green:** Vendors with green lights (i.e., who are low risk) are those who meet the following thresholds: 
    *   No breaches within the last three years
    *   No open `RAs`, findings, or other identified risks

KC's team created a separate database for the data from all the identified sources, which are collected and then utilized by the business intelligence software. The links to these data sources then are created and managed. For the internal vendor risk management software, the `REST API` transfers data on a nightly basis when any changes are made to vendors that are part of the security controls reporting. A `REST API` (also known as `RESTful API`) is an application programming interface (`API` or web `API`) that follows to the constraints of REST architectural style and allows for interaction with RESTful web services. The vendor security monitoring tool also contains a `REST API`, which updates any alerts and data for each vendor. Incident management software tools, threat intelligence applications and feeds, Risk Acceptance data, and the enhanced `CM` data are all then fed into this database as well using either `APIs` or an `ETL` (extract, transform, load) to blend the data from multiple sources into the data store. This database is called the “`Vendor DB`” for references in documentation.

![FIGURE 15.2 Red, Yellow, and Green Vendors](images/c15f002.png)

[FIGURE 15.2](#c15.xhtml#R_c15-fig-0002) Red, Yellow, and Green Vendors

The business intelligence (`BI`) tool then uses the `Vendor DB` for its data, and the triggers and thresholds are programmed into the `BI` tool. The biggest hurdle is often the variances in vendor names. For example, is ABC Corp. the same as ABC Inc.? This likely means a manual process to account for small differences in names. While the `BI` had some logic built into it to attempt to resolve such issues, it places any of these discrepancies (or suspected mismatches) into a separate folder for the analysts to manually intervene and update.

### Use Case #1: Early Intervention

KC's point‐in‐time assessments were previously recognized as leaving large gaps of potential risk in between each of their due diligence activities. It was found that it could be a minimum of 364 days before a vendor's security posture was revalidated. As a result, the team created the `CM` and `ECM` programs, which created ongoing engagements with their vendors based upon leveraging the vendor security rating tools, threat intelligence products, and existing knowledge about the vendor's risk in the systems of record. These programs produced good results as the team saw risk reduction activity based upon the `CM` activities. However, the `Vendor DB` and the `BI` tool provide the ability to identify risk trends from a vendor(s) that goes a bit further than the `CM` model.

ABC Corp. is a vendor for KC that processes past due and collections notices for loans from their customers. ABC has access to personal identifiable information (`PII`) data, which includes names, emails, phone numbers, account information, and in many cases, payment information (i.e., bank account numbers and credit/debit card numbers). While the amount of past due and collections for loans varies month to month, the average is about 10,000 customer `PII` data records annually. This means ABC is placed in the medium‐risk pool. The security reviews at the intake and ongoing assessments produced some findings, but they are closed through remediation and physical validation per their agreements. They have an open `RA` (listed as medium risk per the analysis by the Cybersecurity Third‐Party Risk team) for the lack of a Privileged Access Manager (`PAM`) tool, which shows up on their vendor profile in the `BI` tool. Using the methodology described previously, the vendor has a yellow condition or an elevated risk due to the size and type of data plus the open `RA` at the medium‐risk level. This vendor is not a critical vendor and while they are monitored with the `CM` program, they are not part of the Enhanced `CM` portfolio.
