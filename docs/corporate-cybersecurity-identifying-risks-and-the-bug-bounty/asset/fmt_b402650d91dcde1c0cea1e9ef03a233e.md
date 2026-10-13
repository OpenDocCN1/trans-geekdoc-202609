
# The security researcher who found the vulnerability may not have any intention on the disclosure leaving the “feed” or “stream” in which it was shared with other researchers. If the enterprise is running a private program and participating in limited private disclosure, another researcher may take the report or the findings and leak the report to a journalist or online elsewhere. While the risk of such leakage occurring is exceedingly low, no one should ever assume that it could never happen. Ultimately, the damage that would be caused is one of reputation and not of exploitation as the vulnerability would be fixed. However, in reality, disclosure shouldn’t be looked at as a means of reputation damage. When a program encourages disclosure, the community respects the enterprise far more.

## 2. Disclosure Restrictions

Program managers may decide to avoid disclosure altogether. In any case, the primary occasion in which an enterprise may not want limited disclosure may be due to fears of further exploitation or information leakage, outside of the control of the security researcher or program management.

Disclosure restrictions, at least from the perspective of program managers, are typically a result of immaturity in the bug bounty space. The exploitation of any disclosed report is improbable unless the report reveals more infrastructure or internal information on the program’s private researcher feed. In any case, the information can typically be redacted prior to disclosing.

## 3. Ad Hoc Redactions

A lot of researchers participating in a private program will want disclosure, no matter what policy is currently in place. Security researchers may ask to redact information to be able to include it in their writeup. Instances where disclosure of this form is requested can occur if the enterprise’s program only allows private-stream disclosure, or if the program allows no disclosure.

### The Bottom Line

Security researchers value their research. If redaction can be done to support a researcher’s disclosure, it would be a good incentive to do so in support of their participation. A program manager can write a clause in their program, or respond to researchers if asked, with the following:

> “We will allow public disclosure in writeups. However, please give us the chance to review the writeup to ensure that no potential vectors for exploitation exist. We want you to share the research, but we would like to keep the company safe. We do not want to be overbearing, therefore it will be a light review. If you would prefer not to allow us to review the writeup, we understand and respect the value that you bring to our company. Disclose at will.”

In most cases, a statement of support as defined above will be an adequate method of support for the security researcher’s findings. Without falling subject to the fallacy of a slippery slope, completely preventing any form of public disclosure isn’t useful methodology. Researchers who are avid writers that participate in the public-facing bug bounty community will end up disclosing, and this could result in accidentally disclosing internal information or infrastructure outside of the visibility or control of a program. Nonetheless, while it is an option to ask for redaction of specific aspects of the writeup, this should not be weaponized against a hacker. Redaction should only be done in a way that prevents further exploitation of the service. If a program manager does not feel comfortable with a researcher disclosing their research, they should aim to either improve security or refrain from operating a bug bounty program.

## 8.1.1.2 Public Programs

The subject of public programs represents a different challenge, the “anyone can do it” effect. In other words, an enterprise bug bounty program manager may find increased participation if participating researchers are allowed to disclose. Nearly all aspects of disclosure from private programs carry over to the configuration in public programs, with the exception of one additional feature that is reserved to public programs: full public disclosure.

### 1. Full Public Disclosure

Public programs have the ability to fully commit to the most permissive state of programs: full disclosure. Essentially, when an enterprise program is configured to have the disclosure feature in a public state, security researchers can request disclosure of their patched vulnerabilities, and that means the vulnerability will hit a highly visible state, one in which any person who accesses the crowdsourcing platform can completely see the report (with the desired redacted information).

One of the primary issues with fully public disclosure is the representation of a program’s value and the possibility of increased participation (the anyone can do it effect). Basically, there are several scenarios in which full public disclosure can result in an excessive uptick of participation, primarily when a program discloses a vulnerability that resulted in a big reward or the program releases a chain of reports.

Payday mayday, or in summary, is the disclosure of a report in which a researcher has earned a significant amount of money, which could result in possible press. It’s not unheard of to have a journalist write on the subject of a patched vulnerability, especially if it could have resulted in a significant exploitation or compromise of a user’s data or a company’s product. If a journalist picks up a vulnerability report and writes about it, a surge of researchers may rush to the program hoping for their shot at a big payday. Even though the instance of a vulnerability as critical as the disclosed one being found after the previous one was disclosed is unlikely, it’s not impossible. Secondly, a burst of smaller vulnerabilities may be reported, or even if no greater-than-average amount of vulnerabilities get reported, there could be enterprise disruption as a result of a lot of security research activity being conducted. It’s not a matter of fact that the vulnerability will be picked up by a journalist, but all scenarios should be considered.

Chain report disclosure may not result in press exposure, but comparatively, some similar effects seen in a high-payout scenario could possibly occur, particularly increased security researcher participation or disruptive levels of activity that the enterprise isn’t ready to manage.

### The Bottom Line

Program managers should allow public disclosure and realize that they need to be prepared to deal with a spike in reports, and have thoroughly hardened assets. The public disclosure process shouldn’t be discouraged. However, if the enterprise is not comfortable with disclosure, realize that it’s an uncomfortable event that program managers must get comfortable with. After all, even if the enterprise did not have a program, they face hackers disclosing vulnerabilities to the public. A program at least gives the chance to encourage positive rhetoric and rewards around reporting, giving program managers an edge. Allow researchers to disclose, or do not run a bug bounty program.

## 8.2 CVE Responsibility

### 8.2.1 What are CVEs?

CVEs stand for common vulnerabilities and exposures. The CVE program was developed in 1999 and is sponsored by the US Department of Homeland Security and the Cybersecurity and Infrastructure Security Agency. CVEs were meant to be used as a way of standardizing vulnerabilities and disclosures, linking many databases together in an attempt to make it easier for enterprises to manage and patch newly identified vulnerabilities.

### 8.2.2 Program Manager Responsibilities
