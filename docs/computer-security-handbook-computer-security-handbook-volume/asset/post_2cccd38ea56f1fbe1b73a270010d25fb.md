
- 135. Nathan Thornburgh, “Inside the Chinese Hack Attack,” Time, August 25, 2005, www.time.com/time/nation/article/085991098371,00.html
- 136. John Ribeiro, “Source Code Stolen from U.S. Software Company in India: Jolly Technologies Blamed an Insider for the Theft,” Computerworld, August 5, 2004, www.computerworld.com/s/article/95045/Source_code_stolen_from_U.S._software_company_in_India?taxonomyId=082
- 137. Todd Wallack, “EMC Sues Ex-Employees To Guard Trade Secrets,” Boston Business Journal, October 9, 2006, www.bizjournals.com/boston/stories/2006/10/09/story4.html?page=all
- 138. U.S. Department of Justice, “Two Men Plead Guilty to Stealing Trade Secrets from Silicon Valley Companies to Benefit China,” U.S. Department of Justice | Northern District of California, December 14, 2006, www.justice.gov/criminal/cybercrime/press-releases/2006/yePlea.htm
- 139. Joby Warrick and Carrie Johnson, “Chinese Spy ‘Slept’ In U.S. for 2 Decades: Espionage Network Said To Be Growing,” Washington Post, April 3, 2008, www.washingtonpost.com/wp-dyn/content/story/2008/04/02/ST20080402040450.html
- 140. Siobhan Gorman, “Electricity Grid in U.S. Penetrated By Spies,” Wall Street Journal, April 8, 2009, http://online.wsj.com/article/SB123914805204099085.html
- 141. Office of the National Counterintelligence Executive (ONCIX), “Foreign Spies Stealing US Economic Secrets in Cyberspace: Report to Congress on Foreign Economic Collection and Industrial Espionage, 2009–2011,” Office of the National Counterintelligence Executive, November 3, 2011, www.ncix.gov/publications/reports/fecie.all/Foreign_Economic_Collection_2011.pdf
- 142. Michael Riley and Ashlee Vance, “Inside the Chinese Boom in Corporate Espionage,” Bloomberg Businessweek, March 15, 2012, www.businessweek.com/articles/2012-03-14/inside-the-chinese-boom-in-corporate-espionage
- 143. Symantec, “Internet Security Threat Report 2013,” Symantec, April 15, 2013, www.symantec.com/content/en/us/enterprise/other_resources/b-istr_main_report_v18.2012_21291018.en-us.pdf

## TOWARD A NEW FRAMEWORK FOR INFORMATION SECURITY*

Donn B. Parker, CISSP

- 3.1 PROPOSAL FOR A NEW INFORMATION SECURITY FRAMEWORK 3·1
- 3.2 SIX ESSENTIAL SECURITY ELEMENTS 3·3
  - 3.2.1 Loss Scenario 1: Availability 3·4
  - 3.2.2 Loss Scenario 2: Utility 3·4
  - 3.2.3 Loss Scenario 3: Integrity 3·5
  - 3.2.4 Loss Scenario 4: Authenticity 3·5
  - 3.2.5 Loss Scenario 5: Confidentiality 3·6
  - 3.2.6 Loss Scenario 6: Possession 3·7
  - 3.2.7 Conclusions about the Six Elements 3·8
- 3.3 WHAT THE DICTIONARIES SAY ABOUT THE WORDS WE USE 3·9
- 3.4 COMPREHENSIVE LISTS OF SOURCES AND ACTS CAUSING INFORMATION LOSSES 3·10
  - 3.4.1 Complete List of Information Loss Acts 3·11
  - 3.4.2 Examples of Acts and Suggested Controls 3·14
  - 3.4.3 Physical Information and Systems Losses 3·17
  - 3.4.4 Challenge of Complete Lists 3·18
- 3.5 FUNCTIONS OF INFORMATION SECURITY 3·19
- 3.6 SELECTING SAFEGUARDS USING A STANDARD OF DUE DILIGENCE 3·20
- 3.7 THREATS, ASSETS, VULNERABILITIES MODEL 3·20
- 3.8 CONCLUSION 3·20
- 3.9 FURTHER READING 3·23

### 3.1 PROPOSAL FOR A NEW INFORMATION SECURITY FRAMEWORK.

Information security, historically, has been limited by the lack of a comprehensive, complete, and analytically sound framework for analysis and improvement. The persistence of the classic triad of CIA (confidentiality, integrity, availability) is inadequate to describe what security practitioners include and implement when doing their jobs. We need a new information security framework that is complete, correct, and consistent to express, in practical language, the means for information owners to protect their information from any adversaries and vulnerabilities.

The current focus on computer systems security is attributable to the understandable tendency of computer technologists to protect what they know best—the computer and network systems rather than the application of those systems. With a technological hammer in hand, everything looks like a nail. The primary security challenge comes from people misusing or abusing information, and often—but not necessarily—using computers and networks. Yet the individuals who currently dominate the information security folk art are neither criminologists nor computer application specialists.

This chapter presents a comprehensive new information security framework that resolves the problems of the existing models. The chapter demonstrates the need for six security elements—availability, utility, integrity, authenticity, confidentiality, and possession—to replace incomplete CIA security (which does not even seem to include security for information that is not confidential) in the new security framework. This new framework is used to list all aspects of security at a basic level. The framework is also presented in another form, the Threats, Assets, Vulnerabilities Model, which includes detailed descriptors for each topic in the model. This model supports the new security framework, demonstrating its contribution to advance information security from its current technological stage, and as a folk art, into the basis for an engineering and business art in cyberspace.

The new security framework model incorporates six essential parts:

- 1. **Security elements** of information to be preserved are:
  - Availability
  - Utility
  - Integrity
  - Authenticity
  - Confidentiality
  - Possession
- 2. **Sources** of loss of these security elements of information:
  - Abusers and misusers
  - Accidental occurrences
  - Natural physical forces
- 3. **Acts** that cause loss:
  - Destruction
  - Interference with use
  - Use of false data
  - Modification or replacement
  - Misrepresentations or repudiation
  - Misuse or failure to use
  - Location
  - Disclosure
  - Observation
  - Copying
  - Taking
  - Endangerment
- 4. **Safeguard functions to protect information from these acts:**
  - Audit
  - Avoidance
  - Deterrence
  - Detection
  - Prevention
  - Mitigation
  - Transference
  - Investigation
  - Sanctions and rewards
  - Recovery
- 5. **Methods of safeguard selection:**
  - Use due diligence
  - Comply with regulations and standards
  - Enable business
  - Meet special needs
- 6. **Objectives to be achieved by information security:**
  - Avoid negligence
  - Meet requirements of laws and regulations
  - Engage in successful commerce
  - Engage in ethical conduct
  - Protect privacy
  - Minimize impact of security on performance
  - Advance an orderly and protected society

In summary, this model is based on the goal of meeting owners’ needs to protect the desired security elements of their information from sources of loss that engage in harmful acts and events by applying safeguard functions that are selected by accepted methods to achieve desired objectives. The sections of the model are explained next. It is important to note that security risk, return on security investment (ROSI), and net present value (NPV) based on unknown future losses and enemies and their intentions are not identified in this model, since they are not measurable and, hence, not manageable.

### 3.2 SIX ESSENTIAL SECURITY ELEMENTS.

Six security elements in the proposed framework model are essential to information security. If any one of them is omitted, information security is deficient in protecting information owners. Six scenarios of information losses, all derived from real cases, are used to demonstrate this contention. We show how each scenario involves violation of one, and only one, element of information security. Thus, if we omit that element from information security, we also remove that scenario from the concerns of information security, which would be unacceptable.

It is likely that information security professionals will agree that all of these scenarios fall well within the range of the abuse and misuse that we need to protect against.

#### 3.2.1 Loss Scenario 1: Availability.

A rejected contract programmer, intent on sabotage, removed the name of a data file from the file directories in a credit union’s computer. Users of the computer and the data file no longer had the file available to them, because the computer operating system recognizes the existence of information available for users only if it is named in the file directories. The credit union was shut down for two weeks while another programmer was brought in to find and correct the problem so that the file would be available. The perpetrator was eventually convicted of computer crime.

Except for availability, the other elements of information security—utility, integrity, authenticity, confidentiality, and possession—do not address this loss, and their state does not change in the scenario. The owner of the computer (the credit union) retained possession of the data file. Only the availability of the information was lost, but it is a loss that clearly should have been prevented by information security. Thus, the preservation of availability must be accepted as a purpose of information security.

It is true that good security practice might have prevented the disgruntled programmer from having use of the credit union application system, and credit union management could have monitored his work more carefully. They should not have depended on the technical capabilities and knowledge of only one person, and they should have employed several controls to preserve or restore the availability of data files in the computer, such as by maintaining a backup directory with the names of erased files and pointers to their physical location. The loss might have been prevented, or minimized, through good backup practices, good usage controls for computers and specific data files, use of more than one name to identify and find a file, and the availability of utility programs to search for files by content or to mirror file storage. These safeguards would at least have made the attack more difficult and would have confronted the programmer with the malfeasance of his act.

The severity of availability loss can vary considerably. A perpetrator may destroy copies of a data file in a manner that eliminates any chance of recovery. In other situations, the data file may be partially usable, with recovery possible for a moderate cost, or the user may have inconvenienced or delayed use of the file for some period of time, followed by complete recovery.

#### 3.2.2 Loss Scenario 2: Utility.

In this case, an employee routinely encrypted the only copy of valuable information stored in his organization’s computer and then accidentally erased the encryption key. The usefulness of the information was lost and could be restored only through difficult cryptanalysis.

Although this scenario can be described as a loss of availability or authenticity of the encryption key, the loss focuses on the usefulness of the information rather than on the key, since the only purpose of the key was to facilitate encryption. The information in this scenario is available, but in a form that is not useful. Its integrity, authenticity, and possession are unaffected, and its confidentiality, unfortunately, is greatly improved.

To preserve utility of information in this case, management should require mandatory backup copies of all critical information and should control the use of powerful protective mechanisms such as cryptography. Management should require security walk-through tests during application development to limit unusable forms of information. It should minimize the adverse effects of security on information use and should
