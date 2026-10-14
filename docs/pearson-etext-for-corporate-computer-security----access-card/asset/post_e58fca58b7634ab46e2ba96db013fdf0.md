
33.
a. Why is ethics unpredictable?
b. Why do companies create codes of ethics?
c. Why is good ethics important in a firm?
d. To whom do codes of ethics apply?
e. Do senior officers often get an additional code of ethics?
f. If an employee has an ethical concern, what must he or she do?
g. What must an employee do if he or she observes unethical behavior?
h. What examples of conflicts of interest were given?
i. Why are bribes and kickbacks bad?
j. Distinguish between bribes and kickbacks.
k. What types of information should an employee not reveal?

### Ethics
- A person’s system of values
- Needed in complex situations
- Different people may make different decisions in the same situation
- Companies create codes of ethics to give guidance in ethical decisions

### Code of Ethics: Typical Contents (Partial List)
- Importance of good ethics to have a good workplace and to avoid damaging a firm’s reputation
- The code of ethics applies to everybody
  - Senior managers usually have additional requirements
- Improper ethics can result in sanctions, up to termination
- An employee must report observed unethical behavior
- An employee must avoid conflicts of interest
  - Never exploit one’s position for personal gain
  - No preferential treatment of relatives
  - No investing in competitors
  - No competing with the company while still employed by the firm
- No bribes or kickbacks
  - Bribes are given by outside parties to get preferential treatment
  - Kickbacks are given by sellers when they place an order to secure this or future orders
- Employees must use business assets only for business use, not for personal use
- An employee may never divulge
  - Confidential information
  - Private information
  - Trade secrets

Figure 2-21 Ethics (Study Figure)

## Exception Handling

It would be nice if implementation would never require exceptions from policies or implementation guidance, but occasionally exceptions are necessary. This requires implementation guidance specifications to include guidance on exception handling. Guidance is critical because exceptions are dangerous, so they must be tightly controlled and documented. Below are some general guidelines to handling exceptions.

### Exceptions Are Always Required

### Limiting Exceptions
- Only some people should be allowed to request exceptions
- Fewer people should be allowed to authorize exceptions
- The person who requests an exception must never be the authorizer

### Exception Must Be Carefully Documented

Specifically what was done and who did each action

### Special Attention Should Be Given to Exceptions in Periodic Auditing

### Exceptions above a Particular Danger Level Need to Be Reported

Brought to the attention of IT security department and the authorizer’s direct manager

Figure 2-22 Exception Handling (Study Figure)

- Only some people should be allowed to request exceptions.
- Even fewer people should be allowed to authorize exceptions.
- The person who requests an exception must never be the same person who authorizes the exception.
- Each exception must be carefully documented in terms of specifically what was done and who did each action.
- Special attention should be given to exceptions in periodic auditing.
- Exceptions above a particular danger level should be brought to the attention of the IT security department and the authorizer’s direct manager.

## Test Your Understanding

34. a. Why shouldn’t exceptions be absolutely forbidden?
b. Why is implementation guidance for exception handling necessary?
c. What are the first three rules for exceptions?
d. Why would documentation and periodic auditing be important?
e. What is an example of a dangerous exception that would need to be reported to a manager?

## Oversight

Ideally, policies would be implemented faithfully under the constraints of appropriate implementation guidance. Sadly, that is not always the case. In 2015, a survey of 1,000 federal employees found that 24 percent of workers send work documents to personal e-mail accounts even though they know it is against federal policy to do so.10 Even worse, 40 percent of employees surveyed used a personal smartphone at work despite knowing about a locked-down mobile policy.

10 Lookout, “Lookout Study: Nearly 40 Percent of Government Employees Ignore Policies Prohibiting Mobile Device Use, Put Sensitive Data at Risk,” Lookout.com, August 19, 2015. www.lookout.com/news-and-press/press-releases/lookout-study-nearly-40-percent-of-government-employees-ignore-policies-prohibiting-mobile-device-use-put-sensitive-data-at-risk.

In addition, 58 percent reported that they knew their behaviors created security concerns but chose to violate policies anyway. Why were these violations so common? The respondents may have done so out of convenience or a lack of policy enforcement. Oversight is a process, function, or group of tools that are used to improve policy implementation and enforcement. There are many types of oversight.

> Oversight is a process, function, or group of tools that are used to improve policy implementation and enforcement.

POLICIES AND OVERSIGHT Figure 2-19 shows that policy and oversight are related. Just as a policy drives implementation, the same policy drives oversight. The staff members involved in oversight must develop oversight plans appropriate for a specific policy.

PROMULGATION The first job of security management after creating policies is to make users aware of them. Formally announcing, publishing, or making users aware of a new policy is called promulgation. If users do not know or understand policies, they cannot follow them. It is important to market policies actively and to underscore the vision behind specific policies.

As noted earlier in this chapter, it is useful to have affected users sign policies. This brings a sense of security that heightens awareness.

One controversial way to publicize policies is to conduct stings of employees. In these stings, employees are asked to do something against a policy. For example, a recent study found that 20 percent of employees would click on a phishing e-mail. That rate would go up around the holidays or if the e-mail contained the words “your scanned file.” The click-through rate on phishing e-mails would drop to 0.2 percent if the employees went through five training simulations.

Conducting stings is good for raising awareness. Stings can also be used as a ploy to increase IT security awareness training money. If specific stings are repeated annually, they can also be used to indicate positive trends.

Stings are controversial because they will generate resentment if they are not handled properly. To avoid problems, the identities of the stung employees should never be revealed. In addition, they should only be used as teaching situations and never for punishment.

ELECTRONIC MONITORING In many cases, it is possible to electronically monitor compliance behavior automatically. A recent study found that almost 94 percent of corporations are monitoring employee behavior, and 93 percent monitor employees’ access to sensitive data. Employers are worried about insider threats because of excessive access privileges (37 percent), too many devices with access to data (36 percent), and increasingly complex technology (35 percent). If a firm is going to use electronic monitoring, it is important to inform employees about it ahead of time and explain why it is being done.

SECURITY METRICS Monitoring gives details. Another way to measure compliance is to create security metrics, which are a few well-chosen measurable indicators of security success or failure that are measured periodically. Examples include the

percentage of user PCs left on at night, the percentage of crackable passwords on a server, and the percentage of critical patches applied to webservers. Measuring these metrics periodically indicates whether a company is doing better or worse in implementing its policies.

> Security metrics are measurable indicators of security success or failure.

## AUDITING

All publicly traded companies must have their financial statements audited. Auditing firms do not look at every piece of information that goes into financial statements. Rather, they purposefully sample specific pieces of financial data. On the basis of the sample data, they develop an opinion on how well the financial reporting process is controlled. The purpose of auditing is to develop opinions on the health of controls, not to find punishable instances of noncompliance.

> The purpose of auditing is to develop opinions on the health of controls, not to find punishable instances of noncompliance.

Auditing is only possible if information is recorded. Consequently, most compliance laws and regulations require the extensive recording of information. If the information is recorded in a database, it is called logged information. If the information is recorded on forms or memos, the information is called documentation.

Auditing takes a sample of logged and documented information. In some cases, the auditing will measure the number of times there was noncompliance, for example, if an exception was not authorized. In other cases, the auditor develops metrics, such as the percentage of actions in a certain category that were in violation of the policy.

One key principle is to measure noncompliance events carefully but to focus intensively on every instance in which there is active avoidance of compliance. Avoidance of compliance indicates a deliberate circumvention of security, and always calls for follow-up investigation.

Internal audits are done by the organization itself. External audits are done by an outside firm. In financial auditing, firms are required to have both internal and external auditing. The same is advisable for IT security auditing.

Audits should be scheduled frequently enough to warn of growing dangers. Many firms do IT security auditing quarterly with more rigorous audits once per year. Regularly spaced audits are attractive because they allow a company to compare results over time. However, regularly scheduled audits can work to the advantage of people who are avoiding security. Unscheduled audits therefore are also desirable.

## ANONYMOUS PROTECTED HOTLINE

Companies have long known that the best way to detect frauds and other serious abuse has been to create an anonymous protected hotline. Often it is a coworker who first discovers a security violation.

The 2018 report by the Association of Certified Fraud Examiners found that the best way to detect fraud is through tips. More than 40 percent of fraud is detected through anonymous tips.13 Organizations with anonymous hotlines get more fraud tips (46 percent) than organizations that don’t have an anonymous hotline (30 percent).

13 Association of Certified Fraud Examiners, “Report to the Nations: 2018 Global Study on Occupational Fraud and Abuse,” ACFE.com, April 17, 2019. www.acfe.com/report-to-the-nations/2018.
