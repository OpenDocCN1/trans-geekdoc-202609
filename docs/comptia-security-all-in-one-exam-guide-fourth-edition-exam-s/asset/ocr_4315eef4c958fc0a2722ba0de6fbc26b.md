# Measurement of Availability

Availability is a measure of the amount of time a system performs its intended function. Reliability is a measure of the frequency of system failures. Availability is related to, but different than reliability and is typically expressed as a percentage of time the system is in its operational state. To calculate availability, both the MTTF and the MTTR are needed:

Availability = MTTF / (MTTF + MTTR)

Assuming a system has an MTTF of 6 months and the repair takes 30 minutes, the availability would be

Availability = 6 months / (6 months + 30 minutes) = 99.9884%

factors that exist in a given risk assessment. It is also easy to see that a risk assessment that measures no factors quantitatively but measures them all qualitatively is possible.

The decision of whether to use qualitative versus quantitative risk management depends on the criticality of the project, the resources available, and the management style. The decision will be influenced by the degree to which the fundamental risk management metrics, such as asset value, exposure factor, and threat frequency, can be quantitatively defined.

![](bbox=[0.15, 0.68, 0.25, 0.75])

EXAM TIP Quantitative risk management involves assigning specific absolute values to risk, while qualitative risk management is accomplished with relative values.

# Vulnerabilities

Vulnerabilities are characteristics of an asset that can be exploited by a threat to cause harm. Your system has a security vulnerability, for example, if you have not installed patches to fix a cross-site scripting (XSS) error on your website. Not all errors or bugs are vulnerabilities. For an error or bug to be classified as a vulnerability, it must be exploitable, meaning an attacker must be able to use the bug to cause a desired result. There are three elements needed for a vulnerability to occur:

+   - The system must have a flaw.
+   - The flaw must be accessible by an attacker.
+   - The attacker must possess the ability to exploit the flaw.

Vulnerabilities can exist in many levels and from many causes. From design errors, coding errors, or unintended (and untested) combinations in complex systems, there are numerous forms of vulnerabilities. Vulnerabilities can exist in software, hardware,