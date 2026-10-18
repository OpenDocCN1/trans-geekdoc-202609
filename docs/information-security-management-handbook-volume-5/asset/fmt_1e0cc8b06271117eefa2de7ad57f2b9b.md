
Open Checklist Interactive Language is officially Part of SCAP 1.1 DRAFT located at [`http://scap.nist.gov/specifications/ocil/`](http://scap.nist.gov/specifications/ocil/) The Open Checklist Interactive Language defines a framework for expressing a set of questions to be presented to a user and corresponding procedures to interpret responses to these questions. Although the OCIL specification was developed for use with IT security checklists, the uses of OCIL are by no means confined to IT security. Other possible use cases include research surveys, academic course exams, and instructional walkthroughs.[^‡](#9781466508507_epub_c06_r1.htm#ch6-ftn10)

XCCDF documents are made up of one or more rules. XCCDF rules are usually high-level definitions of technical system (hardware, software, etc.) checks. XCCDF rules are flexible and do not mandate how checks should be performed. In a loosely coupled, tightly integrated design, the rule actually points to other XML documents (e.g., OVAL Definition files) for the granular mechanism and instructions needed to perform the checks. Principally, XCCDF is the list by which everything else runs. It seeks to standardize how security checklists, benchmarks, and related documents are created and then stored. It is the foundation for expression of various checks.

OVAL (as previously mentioned) is a set of definitions broken down into vulnerability, patch, inventory, and compliance. Each defines conditions associated with its realm and are referenced, within the SCAP suite, by XCCDF. OVAL is the what, the why, and sometimes the how. It allows you, deterministically, to run a series of “standards-based syntax” questions against an asset that should return objective measures of current state. Pretty basic, right? It also does a lot more and I will go into that in more depth later.

OCIL is a method and framework that enables systems to be checked that cannot be evaluated without some human interaction or feedback. It accomplishes this basically by presenting questions to its intended users in a standard language format. It includes standard syntax for the questions posed to users as well as instructions that guide those users towards an answer. Additional processes such as acceptance of responses, transfer of artifacts, and eventually evaluation of results are also included. Extrapolating OCIL’s potential, we can easily see that it has far-reaching implications based on the fact that so much of what we do still requires some type of “analog” input from users both within IT and outside of the profession.

# Enumerations

The goal of SCAP enumerations is to provide standards-based naming formats to facilitate open-sharing without having to constantly negotiate definitions between systems. The maintenance of an associated dictionary of items associated with those standards is also critical.

# Common Configuration Enumeration (CCE)

“The Common Configuration Enumeration, or CCE, assigns unique entries (also called CCEs) to configuration guidance statements and configuration controls to improve workflow by facilitating fast and accurate correlation of configuration issues present in disparate domains. In this way, it is similar to other comparable data standards such as the Common Vulnerability and Exposure (CVE) List, which assigns identifiers to publicly known system vulnerabilities.”[^(\*)](#9781466508507_epub_c06_r1.htm#ch6-ftn11)

Did you get that? Basically, as mentioned above there are hundreds and sometimes thousands of settings associated with configurations of software, hardware, firmware, etc. Manually setting these is quickly growing beyond the ability of any organization of any size and this standardization allows for the consumption of configuration management changes in an automatic fashion using XCCDF checklists or OVAL, etc.

# Common Platform Enumeration (CPE) 2.2

“CPE is a structured naming scheme for information technology systems, platforms, and packages. Based upon the generic syntax for Uniform Resource Identifiers (URI), CPE includes a formal name format, a language for describing complex platforms, a method for checking names against a system, and a description format for binding text and tests to a name.”[^†](#9781466508507_epub_c06_r1.htm#ch6-ftn12)

Hand in hand with CCE is the CPE, which enforces a common naming scheme across all hardware and software platforms. The practical application of this is called the CPE dictionary, which is available to the global community. It is currently hosted at the National Vulnerability Database website and is a list of well over 17,000 official CPE product names. The dictionary is in XML format and available to the public via the web. The CPE dictionary is currently generated daily (as needed) to add new products to the dictionary or update existing dictionary entries.

CPE is used by SCAP in the following ways:

![](OEBPS/images/box.jpg) `XCCDF` – In an XCCDF checklist, CPE Names can be used to identify the hardware or software platform to which an XCCDF object (e.g., benchmark, profile, group, rule) applies.

![](OEBPS/images/box.jpg) `CCE` – CPE Names can be associated with configuration vulnerabilities to identify platforms covered by CCE technical mechanisms.

![](OEBPS/images/box.jpg) `CVE` – CVEs are related to one or more product platforms expressed as CPEs. The mapping of CPEs to CVEs is performed by NVD analysts and is published in the NVD vulnerability data feed.[^(\*)](#9781466508507_epub_c06_r1.htm#ch6-ftn13)

# Common Vulnerabilities and Exposures (CVE)

“CVE is a dictionary of unique, common names for publicly known software flaws. This common naming convention allows sharing of data within and among organizations and enables effective integration of services and tools.”[^†](#9781466508507_epub_c06_r1.htm#ch6-ftn14)

The CVE was created principally to address the differences in vulnerability names and descriptions. The inconsistency of schemas and naming conventions as well as descriptors in the past had created a great deal of confusion. Anyone that adheres to the CVE naming conventions, which is required to use SCAP effectively, is able to use terms that all security practitioners can agree mean the same thing. While this may seem like a fairly basic concept, believe me it is not. To get an idea of how the profession has communicated in the past, just imagine the Tower of Babel in the Bible, but worse.

A significant practical application of standard naming involving both CPE and CVE is illustrated by the National Vulnerability Database. John Banghart nut-shelled the concept and detailed the actual real-world application, its benefits, and its scope as currently implemented.

![](OEBPS/images/fig_83-1.jpg)

**Schmidt wrote:**

# National Vulnerability Database

The NVD is the federal government repository of standards-based vulnerability management reference data. The NVD contains information regarding vulnerabilities (software flaws and misconfigurations), including impact measurements, detection techniques, remediation assistance, and security control mappings. NVD search and publication capabilities provide access to all publicly available federal vulnerability resources and references to industry resources. NVD also contains a statistics engine to enable users to gain a deeper scientific understanding of the nature of published vulnerabilities and associated trends. NVD supports SCAP by making SCAP standard reference data readily available to industry and government agencies.

# Vulnerability Search Engine
