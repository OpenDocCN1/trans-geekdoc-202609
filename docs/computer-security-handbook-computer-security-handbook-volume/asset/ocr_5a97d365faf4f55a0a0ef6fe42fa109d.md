network-based detection is to analyze network flow (netflow) data in comparison with a statistical database of known good traffic. However, malicious code that acts normal can bypass such methods of detection. Predicting what is normal for a given environment may be difficult for an outsider, but analyzing certain activity like domain name system, email, and Web usage can produce generic models for evasion.

# 16.4.3 Behavioral Malicious Code Detection.

Behavioral methods of detecting malicious code analyze the actions of running software to look for illegitimate activity. This could be opening a port, connecting to a remote host, or modifying the system call table or other memory areas. Behavioral methods of detection will fail if the malware acts normal or if the malicious code can target and exploit the detection system itself. A slow but effective method of detecting potentially malicious code is to use a virtual machine approach, whereby the system allows code to execute in a sandboxed virtual machine. This allows for a full functional analysis of the code, but the current throughput of such systems makes them not useful for today's high-speed production environments.

# 16.4.4 Heuristic Malicious Code Detection.

Heuristics that are more complex may use both statistical and behavioral models to determine a relative score to a normal corpus (statistical database in this case) of legitimate behavior. Bayesian analysis is widely used in the detection of spam. However, this method can also detect new variants of existing malicious code with a high degree of accuracy. N-gram analysis is a form of frequency analysis borrowed from natural language processing that can model software and fingerprint data types. This method is useful for detecting executable code embedded within other data objects. In short, there is no single, monolithic way to detect all malicious code. Spinellis demonstrated that reliable detection of malicious code is NP-complete,⁴⁹ meaning that the dilemma is not solvable in polynomial time. However, the technologies discussed, used in concert, are relatively effective in detecting many common malicious code threats.

# 16.5 PREVENTION OF MALICIOUS CODE ATTACKS

# 16.5.1 Defense in Depth.

As the problem of malicious code is demonstrably NP-complete (not solvable), a single antivirus program cannot protect against all malicious code threats. One strategy, called defense in depth, uses operational, human, and technical controls. Another strategy is to build networks and applications that only function one correct way. Such orthogonal networks and applications are a rarity as they are expensive and difficult to design, and many firms will resist imposing rigid limitations on the enterprise.

# 16.5.2 Operational Controls for Malicious Code.

All organizations must create written policies and procedures regarding the introduction of program code into the operating environment. Policies should define what persons the firm allows to install programs, acceptable use for Internet access, acceptable use for email systems, and what to do if users suspect the compromise of a system or user. Organizations should subject all new employees to some level of background investigation. This should include, at a minimum, a criminal records search, verification of all references and credentials, and a credit report. Employers should ensure that the prospective employees are forthright and truthful on their application. If employees lie prior to employment, the odds are that they will lie later as well.