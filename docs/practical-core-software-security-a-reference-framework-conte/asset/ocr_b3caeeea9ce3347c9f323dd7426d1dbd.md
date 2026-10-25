application compared to another. It could be because developers in the former were better trained or implemented the framework more effectively. Such feedback should be looped back into earlier stages of the SDL during the next release cycle.

# ## Remediation Report

A remediation report/dashboard should be prepared and updated regularly from this stage. The purpose of this report is to showcase the security posture and risk of the product at a technical level.

# ## 6.7 Metrics

The following metrics should be collected during this phase of the SDL (some of which may overlap metrics we discussed earlier).

+   - Percent compliance with company policies (updated)
+     - Percent of compliance in Phase 3 versus Phase 4
+   - Number of lines of code tested effectively with static analysis tools
+   - Number of security defects found through static analysis tools
+   - Number of high-risk defects found through static analysis tools
+   - Defect density (security issues per 1000 lines of code)
+   - Number and types of security issues found through static analysis, dynamic analysis, manual code review, penetration testing, and fuzzing
+     - Overlap of security issues found through different types of testing
+     - Comparison of severity of findings from different types of testing
+     - Mapping of findings to threats/risks identified earlier
+   - Number of security findings remediated
+     - Severity of findings
+     - Time spent (approximate) in hours to remediate findings
+   - Number, types, and severity of findings outstanding
+   - Percentage compliance with the security test plan
+   - Number of security test cases executed
+     - Number of findings from security test case execution
+     - Number of retests executed

# ## 6.8 Summary

During our discussion of the design and development (A4) phase, we described the process for successful test case execution, the process of proper code review through the use of both automated tools and manual review, and the process for privacy validation and remediation to be conducted during this phase of the SDL. The most critical processes and procedures described in this chapter are those that provide the ability to effectively and efficiently test, tune, and remediate known vulnerabilities and to ensure that secure coding policies have been followed, which provide the necessary security and privacy vulnerability protections before moving on to the product ship (A5) phase of the SDL.