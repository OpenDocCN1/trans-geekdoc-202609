
Within this tab, there isn’t much to cover. An option to turn swag awards on or off is available. If you don’t know what swag is, it’s basically company-branded apparel or items that programs can opt to give out to hackers for participating in the program.

### 6.3.3.17 Common Responses

When managing a bug bounty program, enterprises will find an annoyance in out-of-scope or nonvulnerable/unqualifying vulnerability reports. The “Common responses” tab provides an easy way for program managers to add custom responses to mitigate considerable nonissues that are reported to the program ([Figure 6.82](#c06.xhtml#c6-fig-0082)).

![Figure 6.82 Common reponses option.](images/c06f082.png)

[**Figure 6.82**](#c06.xhtml#rc6-fig-0082) Common reponses option.

The common responses automation can assist with more than just dealing with out-of-scope vulnerabilities. Program managers can create automations for any scenario, including a ticket changing from open to triage, or closing tickets. For example, a program manager may want to automate a common response that congratulates a researcher for participating when they are rewarded, and so on.

To create a flow, follow the following steps.

Click on the “Add Common Response” button ([Figure 6.83](#c06.xhtml#c6-fig-0083)):

![Figure 6.83 Add common response option.](images/c06f083.png)

[**Figure 6.83**](#c06.xhtml#rc6-fig-0083) Add common response option.

Create the flow, set the title to something that can be remembered. As an example it could be a decent idea to title a common response as “Reward Response,” and in the message field a program manager can type a message to send to a hacker after rewarding them, such as “Thank you for participating in our program! We encourage you to keep hacking!” or whatever seems like a good fit ([Figure 6.84](#c06.xhtml#c6-fig-0084)).

![Figure 6.84 Edit common response option.](images/c06f084.png)

[**Figure 6.84**](#c06.xhtml#rc6-fig-0084) Edit common response option.

Once the response is saved, a program manager can click on the “Default Common Responses” button to set a common response to an action ([Figure 6.85](#c06.xhtml#c6-fig-0085)):

![Figure 6.85 Default common responses option.](images/c06f085.png)

[**Figure 6.85**](#c06.xhtml#rc6-fig-0085) Default common responses option.

As seen, nearly any ticketing action can be utilized in conjunction with common responses. Program managers can creative baseline responses to help assist in day-to-day workflows, but it isn’t a requirement of a successful program.

### 6.3.3.18 Triggers

The “Triggers” tab offers similar functionality to the common responses tab. However, it offers more specific wording and tuning. Enterprises can configure default rules that elicit specific responses when keywords or fields are matched. The triggers are written as basic if/then statements. Program managers can combine a wide variety of options, even multiple options to make up the various triggers. Observe the following example ([Figure 6.86](#c06.xhtml#c6-fig-0086)):

![Figure 6.86 Create triggers option.](images/c06f086.png)

[**Figure 6.86**](#c06.xhtml#rc6-fig-0086) Create triggers option.

The above is broken into simple statements, and two rules were added to show how it can be utilized. First, a program manager must select what their triggering event is. So, in this instance, if the report weakness contains a use of hard-coded credentials, and the report severity contains critical, then a comment will be added to all participants in the program (bug bounty program managers and hackers) stating, “If you do not get a response in thirty minutes, please contact our emergency response team at 123-123-1234.” There are many ways in which triggers can be used to increase the effectiveness of programs.

### 6.3.3.19 Integrations

In all, the HackerOne program options allow for more integrations than Bugcrowd. Additionally, similar to Bugcrowd, documentation for the integrations exist and can be utilized as a means of understanding the ins and outs of configuration. Again, as there are a lot of options and some are fairly specific, they are not discussed individually in this chapter.

### 6.3.3.20 Api

The API settings are straightforward and are also identical in many senses to Bugcrowd’s API features.

### 6.3.3.21 Hackbot

Settings within the “Hackbot” tab enable the automation of specific actions and triggers within the bug bounty program. For the most part, all of the various settings are concise and program managers can decide what level of option functionality makes sense for their situation ([Figure 6.87](#c06.xhtml#c6-fig-0087)).

![Figure 6.87 Hackbot settings option.](images/c06f087.png)

[**Figure 6.87**](#c06.xhtml#rc6-fig-0087) Hackbot settings option.

### 6.3.3.22 Export Reports

The ability to export reports is simple. A program manager only has to enter in their email and all of the reports will be emailed to them ([Figure 6.88](#c06.xhtml#c6-fig-0088)). All of the vulnerability reports will take some time to process, and then when it’s done the reports will be available for download as a CSV file.

![Figure 6.88 Export reports option.](images/c06f088.png)

[**Figure 6.88**](#c06.xhtml#rc6-fig-0088) Export reports option.

### 6.3.3.23 Profile Settings

The profile settings page is fairly standard and all in all isn’t much different from other configurations. HackerOne is a little bit more unique in the sense that it blends researcher and program manager preferences together.

### 6.3.4 Inbox

Program managers will spend the majority of their time within the inbox, working on resolving reported vulnerabilities. The left-hand side of [Figure 6.89](#c06.xhtml#c6-fig-0089) represents a preview of all reports within the program, starting with the new and unassigned reports. Several tabs exist for filtering reports, primarily by new reports that haven’t been addressed, reports that need resolution, reports that need retesting, and reports that are considered “missed targets.” The last tab of the top inbox panel is the “All” tab. It contains the historical contents of every report that has been submitted through the program.

![Figure 6.89 Reporting inbox vulnerabilities.](images/c06f089.png)

[**Figure 6.89**](#c06.xhtml#rc6-fig-0089) Reporting inbox vulnerabilities.

An example report is shown in [Figure 6.90](#c06.xhtml#c6-fig-0090).

#### 6.3.4.1 Report Details

![Figure 6.90 Example report.](images/c06f090.png)

[**Figure 6.90**](#c06.xhtml#rc6-fig-0090) Example report.

The fields that the report contains will change based on the platform that a program manager uses. However, many pieces repeat. For example, the “State” simply defines what phase the submission is in, the “Severity” is the criticality, the “Asset” is what the hacker is reporting on, etc.

#### 6.3.4.2 Timeline

The portion of the report in which a hacker proves to the program that there’s a legitimate proof of concept for the vulnerability is the “timeline.” In short, the timeline is the overall justification including the description of the vulnerability, presumed impact caused, and the steps to replicate ([Figure 6.91](#c06.xhtml#c6-fig-0091)). The timeline is also used as a means to address any vulnerabilities that are reported. Bug bounty program managers can click on the various functions and reward hackers, add comments, close reports, etc.

![Figure 6.91 Timeline option.](images/c06f091.png)

[**Figure 6.91**](#c06.xhtml#rc6-fig-0091) Timeline option.

## 6.4 Summary
