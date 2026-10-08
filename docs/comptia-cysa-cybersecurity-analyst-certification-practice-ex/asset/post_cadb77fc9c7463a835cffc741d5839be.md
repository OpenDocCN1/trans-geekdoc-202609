
- C is correct. A network appliance is essentially a customized server, performing some specialized function, such as web proxy or caching server.

- A, B, and D are incorrect. Network appliances are generally servers, more than wireless access points, endpoints, or virtual hosts.

## 25. Stuxnet, which targeted the uranium enrichment centrifuges run in Iran, was an example of malware targeting what type of system?

- A. VM
- B. ICS
- C. HMI
- D. NAC

- B is correct. The malware Stuxnet, written solely to attack the uranium enrichment program in Iran, specifically targeted the industry control system (ICS) running within the facility.

- A, C, and D are incorrect. Stuxnet didn't target a VM (virtual machine), a human-machine interface (HMI), or any network access control (NAC).

## 26. What type of system presents a unique challenge in updating due to how critical its uptime is?

- A. HVAC
- B. Finance server
- C. SCADA
- D. Perimeter network protection

- C is correct. SCADA systems typically allow for no downtime because they provide critical services. No allowable downtime means no maintenance for updates or patching.

- A, B, and D are incorrect. A is incorrect because HVAC (heating, ventilation, and air conditioning) is not exactly critical infrastructure. B is incorrect because finance servers would be permitted some downtime for patching. D is incorrect because perimeter network protection devices would certainly need to be up to date and would probably include some level of redundancy to allow for downtime.

## 27. An employee has come to you about installing a software package on their desktop. When you ask how confident they are that the software is secure and from a safe vendor, the employee assures you the package was “signed by a certificate.” However, the employee mentioned that during the installation an error appeared, complaining about the signing certificate, but they clicked the error too quickly to actually understand it. A dialog box is still on the desktop screen, showing additional information about the certificate. From Figure 6-1, can you determine the likely error was?

- A. The certificate has expired.
- B. The certificate is from an untrusted source.
- C. The certificate is based on inadequate encryption.
- D. The certificate fingerprint is invalid.

![](img/912de63e2fcf2d66d271d898c9165f4e_177_0.png)

Figure 6-1 Certificate details

- A is correct. From the dates, you see the certificate has expired.

- B, C, and D are incorrect. B is incorrect because the certificate is from a known issuer. C is incorrect because SHA256 is an adequate level of encryption. D is incorrect because there is no way to determine whether the fingerprint is fine just from viewing this dialog box.

## 28. Over the past year, a few significant changes occurred in a company's IT environment. See Figure 6-2 for a list of those changes. Each change had an effect on vulnerability scan reporting. Looking at Figure 6-3, can you determine what change most affected the trend of critical vulnerabilities?

- A. BYOD policy update
- B. Firewall update
- C. Router update
- D. New AVS

| Time | Policy Change |
|---|---|
| Dec-17 | BYOD policy update |
| Mar-18 | Firewall update |
| Mar-18 | Router update |
| May-18 | New AVS |

**Figure 6-2** Documented changes

![](img/912de63e2fcf2d66d271d898c9165f4e_179_0.png)

### Figure 6-3 Vulnerability scan history

- A is correct. Trend analysis shows a sharp decline in critical vulnerabilities in December 2017. That month correlates to an update in the BYOD (bring your own device) policy.

- B, C, and D are incorrect. Critical vulnerabilities showed no increases or declines during these other changes.

## 29. “Bring Your Daughter to Work Day,” cybersecurity analyst Elizabeth brings her daughter to the data center. Paige is curious why analysts across different companies and countries take the same steps to harden their infrastructures. What is Elizabeth’s likely explanation?

- A. Requirements are forced by regulatory compliance.
- B. Policy is dictated by trends.
- C. All analysts trust each other’s good judgment.
- D. Best practices are being widely adopted.

- D is correct. A general adoption of best practices means similar implementation of steps toward hardening the environment, regardless of location and industry.

- A, B, and C are incorrect. A is incorrect because only a subset of environments would be bound by regulatory compliance. **B** is incorrect because trends may influence policy changes but wouldn't create some worldwide common trend. **C** is incorrect because security is not inspired or strengthened by trust.

## 30. A company is experiencing a substantial increase in incidents since allowing de employees to connect their mobile devices to the internal network. What is the key vulnerability behind this scenario?

- A. Mobile devices are being allowed without any corporate policies.
- B. Mobile devices are being used without a VPN connection.
- C. Mobile devices are allowed to be plugged into USB ports on desktop PCs
- D. The network infrastructure is burdened with additional traffic.

- **A** is correct. The main vulnerability starting with a BYOD policy is the unknown status of all personally managed devices. Some will not be adequately patched or updated. Some will have malware already installed. And some may be compromised.

- **B, C, and D** are incorrect. **B** is incorrect because a VPN still means you're connected to the network, whether on-site or remotely. **C** is incorrect because although this USB policy for desktop PCs would further increase the vulnerability of rogue devices on the network, **D** is incorrect because the additional load on the network is likely not that that significant.

## 31. Using the Windows registry editor, a security analyst navigates to the following key:

```
HKLM\Software\Policies\Microsoft\Windows\CurrentVersion\Internet Settings
```

At that key, the analyst sets the value **PreventIgnoreErrors** to **REG_DWORD = 1**. What is the vulnerability that encouraged this setting?

- A. The Certificate Authority is employing too weak a cryptographic.
- B. Users are ignoring certificate errors.
- C. The Certificate Authority is untrusted.
- D. Users' devices are unable to send OSC request.

- **B** is correct. This registry entry, when set to 1, stops users from bypassing certificate errors. A certificate error could be due to any number of issues, such as name mismatch on the certificate, the certificate having expired, or the certificate having inadequate strength.

- **A, C, and D** are incorrect. **A** is incorrect because an overly weak cipher is only one of reasons an error getting. But the registry change directly changes users’ ability to ignore errors. **C** is incorrect because untrusted CA is only one of many causes for errors. **D** is incorrect because OSC request failures are not likely to prompt a registry change as a fix.

## 32. You've learned of a new, critical vulnerability that was discovered late night. You suspect your infrastructure is particularly vulnerable. You need to perform an immediate scan to identify all the affected servers that will require action. What has your attention first?

- A. SIEM
- B. VM management interface
- C. Vulnerability feed
- D. CVSS

- C is correct. You first need to find out if your vulnerability feed already has the ability to scan for and identify this vulnerability. Regardless of whether your external AVS (authorized vulnerability scanner) or in-house scanner is used, it is not guaranteed the scan will be up to date on the most recent.

- A, B, and D are incorrect. A is incorrect because SIEM might inform you of incidents caused by a result of the new vulnerability, but that would be a job for incident response. Your job is to identify and mitigate the new critical vulnerability. B is incorrect because you do not need to manage the VMS right now. D is incorrect because CVSS probably hasn't had a chance to analyze the new vulnerability yet.

## 33. The Authentication metric, the Access Complexity metric, and the Access Vector metric are all scoring factors used for what system?

- A. NVD
- B. PCI DSS
- C. Nessus
- D. CVSS

- D is correct. The Common Vulnerability Scoring System uses these metrics, among others, to calculate a rating for every vulnerability.

- A, B, and C are incorrect. A is incorrect because NVD provides two vulnerability feeds but is not a scoring authority like CVSS. B is incorrect
