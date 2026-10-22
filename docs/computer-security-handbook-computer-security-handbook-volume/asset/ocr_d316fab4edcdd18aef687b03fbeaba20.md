+   - Application design
+   - Network bandwidth

Slow operation can depend on (but is not limited to) the OS, the other applications running, memory saturation and thrashing (excessive swapping of memory contents to virtual memory on disk or on other, relatively slow, memory resources such as flash drives), memory leakage (the failure to de-allocate memory that is no longer needed), disk I/O inefficiencies (e.g., reading single records from very large blocks), and program conflicts (e.g., locking errors). For more information on program performance.

At another level, performance suffers when program designs make it difficult to change their functionality in response to changing requirements. In a database design, defining a primary index field that determines the sequence in which records are stored on disk can greatly speed access to records during sequential reads on key values for that index—but it can be counterproductive if the predominant method for accessing the records is sequential reads on a completely different index.

# 38.4.1.15 Output Format.

Output format errors can be frustrating and time consuming. An error is considered to have occurred when the user cannot change fonts, underlining, boldface, and spacing that influence the final look of the output; alternatively, delays or errors when printing or saving document may occur. Errors occur when the user cannot control the content, scaling, and look of tables, figures, and graphs. Additionally, there are output errors that involve expression of the data to an inappropriate level of precision.

# 38.5 ASSURANCE TOOLS AND TECHNIQUES.

The security community has known about buffer overflow vulnerabilities, as an example, for the past 25 or 30 years, yet the vulnerabilities are still increasing. For example, the National Vulnerability Database reported 418 new buffer overflow errors in 2013 compared with 392 in 2011. Clearly, greater efforts are necessary to teach and to enforce awareness, implementation, and testing of source code.

# 38.5.1 Education Resources.

Build Security In (BSI) is a project of the Software Assurance program of the Strategic Initiatives Branch of the National Cyber Security Division (NCSD) of the U.S. Department of Homeland Security. BSI (http://buildsecurityin.us-cert.gov) contains and links to best practices, tools, guidelines, rules, principles, and other resources that software developers, architects, and security practitioners can use to build security into software in every phase of its development. BSI content is based on the principle that software security is fundamentally a software engineering problem and must be addressed in a systematic way throughout the software development life cycle.

In addition to BSI, and out of the multitudes of sites on the Web that address some facet of secure coding, some sites are listed next to assist in secure application development:

+   - Carnegie-Mellon Software Engineering Institute: www.cert.org/secure-coding
+   - FreeBSD Security Information: www.freebsd.org/security/security.html
+   - International Systems Security Engineering Association (ISSEA): www.issea.org
+   - Open Web Application Security Project: www.owasp.org