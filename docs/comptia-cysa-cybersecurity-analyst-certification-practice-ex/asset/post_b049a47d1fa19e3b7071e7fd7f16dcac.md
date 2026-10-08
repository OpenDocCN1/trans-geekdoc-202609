
14. A
15. D
16. A
17. B
18. D
19. A
20. A
21. B
22. C
23. A, C
24. C
25. B
26. C
27. A
28. A
29. D
30. A
31. B
32. C
33. D
34. B
35. D
36. A
37. A, C
38. C

# IN-DEPTH ANSWERS

## 1. What are the most important types of results to identify from a vulnerability scan report? (Choose two.)

- A. False positives
- B. False negatives
- C. Policy validation
- D. Exceptions to policy

- A and D are correct. The two early results to identify in a scan report are false positives and policy exceptions. After factoring out false positives (those that seem like a vulnerability but are not) and policy exceptions (those that are authorized), then the remaining vulnerabilities need responses.

- B and C are incorrect. B is incorrect because false negatives are not identified and hence not to found on the report. C is incorrect because policy validation does not make sense.

## 2. What is the main purpose of the report after a vulnerability scan is complete?

- A. It is to be analyzed by the cybersecurity team responsible for the scan.
- B. It is used to evaluate the team responsible for the target environment.
- C. It is included in the full report given to executive management.
- D. It is used as a baseline for future vulnerability scans.

- A is correct. The first goal is to analyze the report. That is by the team responsible for the scan.

- B, C, and D are incorrect. B is incorrect because evaluating the internal team is not a responsibility of the scan team. C is incorrect because although the results will go in the final report, merely inserting the results is obviously not the primary goal. D is incorrect because, again, it's not a primary goal, even though the scan might act as a baseline for future scans, or be compared against a prior scan.

## 3. A outcome that at first seems suspicious but later proves to be neutral called what?

- A. False negative
- B. True positive
- C. True negative
- D. False positive

- D is correct. A false positive is a result that seems suspicious or valid at first, but later investigated is deemed not an issue.

- A, B, and C are incorrect. A is incorrect because a false negative is a genuine vulnerability that escapes being reported. B is incorrect because a true positive is a silly answer. C is incorrect because a true negative is also a silly answer.

## 4. When it comes to prioritizing report outcomes, which of the following would you consider when deciding on response actions? (Select all that apply.)

- A. True negatives
- B. False positives
- C. Policy exceptions
- D. Validated vulnerabilities

- A and D are correct. True negatives (genuine, reported vulnerabilities) will be evaluated for responses. The same goes for validated vulnerabilities.

- B and C are incorrect. B is incorrect because false positives should be identified and removed from consideration because they are not actual vulnerabilities. The same goes for C, policy exceptions, because they are authorized to remain as vulnerabilities.

## 5. Vulnerability scanning does not always return reliable and accurate results. The results depend heavily on the systems being scanned. Which of the following systems would be the least likely to be identified and return genuine scan results? (Choose two)

- A. CCTV camera, web-enabled with embedded Apache
- B. An open source firewall, customized by the scan target client
- C. Windows 2012 server, missing three months of patches and the latest Service Pack
- D. Novell NetWare 6.5

- A and B are correct. Devices with embedded Apache server or lightweight versions of Linux to be especially challenging targets. Likewise, the firewall, customized by the customer, may present a unique profile to the scanner.

- C and D are incorrect. C is incorrect because the Windows server is a standard, well-known system for the scanner, and likely to produce fairly reliable results. Similarly for D, the NetWare system should be a recognizable target.

## 6. Alongside the results in the scan report, it's common to refer to external sources such as OSVDB and NVD. What is the reason for vulnerability scanners to include information from those databases?

- A. The sources provide validation to the scan results.
- B. The sources offer additional information and possibly mitigating actions.
- C. The sources provide links to upload sanitized data from the scan.
- D. The sources specify whether a result is a false positive or a genuine vulnerability.

- B is correct. These databases provide additional information and sometimes mitigating solutions.

- A, C and D are incorrect. A is incorrect because the databases cannot validate your findings. C is incorrect because the results would not be uploaded to such stores. D is incorrect because such databases do not help validate or confirm a result as a false positive.

## 7. What is primary value of STIGs and NSA guides?

- A. They are a source of “best practice” principles.
- B. They are a proven source of vulnerability validation steps.
- C. They provide checklists detailing regulatory compliance.
- D. They provide configuration guides for secure networking.

- A is correct. STIGs (Security Technical Implementation Guides) and NSA guides are a source of “best practice” principles.

- B, C, and D are incorrect. B is incorrect because they are not primarily a source for validation steps. C is incorrect because while they may have checklists, that is not their primary value. D is incorrect. 

## 8. Which of the following are good sources of validating scan results? (Choose all that apply.)

- A. Interviewing the system owner
- B. Reviewing the system’s logs
- C. Comparing against past reports
- D. Examining system and network data 

- B and D are correct. Reviewing the system’s logs is a good way of validating results. Also, checking system and network data such as open ports and services is another method for validating results.

- A and C are incorrect. A is incorrect because the system owner might really believe a service isn't running. C is incorrect because although comparing against past reports may show a trend, doesn’t really validate results.

## 9. What method allows the security team to tailor mitigation strategies, evaluate how effective these strategies are, and see the change of controls over time?

- A. Comparing a system against similar systems in the environment
- B. Comparing the current system against the original image, when available
- C. Comparing the system's trend in vulnerabilities
- D. Comparing the results with the system's logs

- C is correct. Comparing the system over time, or how the vulnerabilities trend, is a likely feature in the vulnerability scanner.

- A, B, and D are incorrect. A is incorrect because every system is unique. Comparing against other systems to make decisions is not recommended. B is incorrect because comparing against the original image would be very misleading. D is incorrect because comparing reported with system logs helps validate results but doesn't give much value over time.

## 10. What is best described as comparing a scan report against the personal and documented notes of the scan operator? Such notes would include scanning steps as well as observations around the scan devices' configuration and operation.

- A. Trending the results
- B. Validating the results
- C. Reconciling the results
- D. Managing the results

- C is correct. Reconciling involves comparing the scan report findings with the scan operator's notes and observations. It is critical to take detailed notes; these are invaluable for verifying and validating the report.

- A, B, and D are incorrect. A is incorrect because trending the results is not the same as comparing results to notes. B is incorrect because validating the results sounds reasonable but is not as thorough as reconciling against the operator's notes. D is incorrect because managing the results is not a sensible term.

## 11. What type of scanning target would commonly have vulnerabilities due to the existence of unnecessary services and open ports?

- A. IDS
- B. SCADA device
