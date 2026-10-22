
- Although ActiveX security measures are available in Internet Explorer, other client software may run controls without necessarily implementing such security. Internet Explorer security levels tend to be all or nothing, making it difficult to allow a specific control without allowing all controls of that type. Remote activation of controls can bypass normal security perimeters such as those imposed by firewalls.
- There is no basis for deciding whether a particular control is safe to execute or not, in any particular context.
- Scripting Concerns
  - Lacking a general basis for limiting the actions of controls, ActiveX programmers must effectively determine their own precautions to prevent harmful actions. It is difficult enough to develop a good set of boundaries on program activity, even if one uses a general model such as the sandbox described later; it is extremely difficult to see how individual developers can be expected or, more importantly, trusted to create their own equivalent of the sandbox for each individual control. In light of these hazards, the authors of the CERT/CC report stated that “there is a large number of potential failure points.”

## 17.2.4 Case Studies.

Several security breaches or demonstrations mediated through ActiveX have occurred since the introduction of this technology in the mid-1990s.

### 17.2.4.1 Internet Exploder.

In 1996, Fred McLain wrote Internet Exploder, an ActiveX control designed to illustrate the broad degree of trust conferred on an ActiveX control by virtue of its having been signed. Exploder, when downloaded for execution by Internet Explorer, will shut down the browser’s computer (the equivalent of the Shut down | Shut down sequence from the Start menu on a Windows system). This operation is operationally disruptive but does not actually corrupt the system. McLain notes in his frequently asked questions (FAQ) on Exploder that it is easy to build destructive or malicious controls.28

Exploder raises an important question: Who and what are the limits on trust when using signed code? In normal commercial matters, there is a large difference between an inauthentic signature, a forgery, and a properly signed but unpayable check. In software, the difference between an inauthentic control and a dangerous one is far less clear.

### 17.2.4.2 Chaos Computer Club Demonstration.

On January 27, 1997, a German television program showed members of the Chaos Computer Club demonstrating how they could use an ActiveX control to steal money from a bank account. The control, available on the Web, was written to subvert the popular accounting package Quicken using what amounts to an electronic version of tailgating. A victim need merely visit a site and download the ActiveX control in question; the control then automatically checked to see if Quicken was installed. If so, the control ordered Quicken to issue a transfer order to be saved in its list of pending transfers. The next time the victim connected to the appropriate bank and sent all pending transfer orders to the bank, all the transfers would be executed as a single transaction. The user’s personal identification number (PIN) and transaction authorization number (TAN) would apply to all the transfers, including the fraudulent one in the pile of orders. Most victims would be unaware of the theft until they received their next statement—if then.²⁹

Dan Wallach of Princeton University, commenting on this case, wrote:

> > When you accept an ActiveX control, you're allowing completely arbitrary code to rummage around your machine and do anything it pleases. That same code could make extremely expensive phone calls, to 900 numbers or over long distances, with your modem; it can read, write, and delete any file on your computer; it can install Trojan horses and viruses. All without any of the subterfuge and hackery required to do it with Java. ActiveX hands away the keys to your computer.³⁰

Responding to criticisms of the ActiveX security model, Bob Atkinson, architect and primary implementer of Authenticode, wrote a lengthy essay explaining his point of view. Among the key points:

- Microsoft never claimed that it would certify the safety of other people’s code.
- Authentication is designed solely to permit identification of the culprits *after* malicious code is detected.
- Explorer-based distribution of software is no more risky than conventional purchases through software retailers.³¹

Subsequent correspondence in the RISKS Forum chastised Mr. Atkinson for omitting several other key points, such as:

- Interactions among ActiveX controls can violate system security even though individual controls appear harmless.
- There is no precedent in fact for laying liability at the feet of software developers even when you can find them.
- Under attack, evidence of digital signature is likely to evaporate from the system being damaged.
- Latency of execution of harmful payloads will complicate identification of the source of damage.
- Malice is not as important a threat from code as incompetence.
- Microsoft has a history of including security-threatening options, such as automatic execution of macros in Word, without offering any way of turning off the feature.
- A Web site can invoke an ActiveX control that is located on a different site or that already has been downloaded from another site, and can pass, by means of that control, unexpected arguments that could cause harm.³²

Wallach’s criticisms of ActiveX are generally applicable to signed code technologies, not peculiar to Microsoft’s ActiveX.

### 17.2.4.3 Certificates Obtained by Imposters.

In January 2001, VeriSign issued two Class 3 Digital Certificates for signing ActiveX controls and other code to someone impersonating a Microsoft employee. As a result, users receiving code signed using these certificates would receive a request for acceptance or rejection of a certificate apparently signed by Microsoft on January 30 or 31, 2001. As Russ Cooper commented on the NTBUGTRAQ Usenet group when the news came out in March 2001:

The fact that unless you actually check the date on the Certificate you won’t know whether or not its [sic] one you can trust is a Bad Thing(im)[sic], as obviously not everyone (read: next to nobody) is going to check every Certificate they get presented with.

You gotta wonder how VeriSign’s issuance mechanism could be so poorly designed and/or implemented to let something like this happen.

Meanwhile, Microsoft are [sic] working on a patch that will stick its finger in this dike.

Basically, VeriSign Code-Signing Certificates do not employ a Certificate Revocation List (CRL) feature called CDP, or CRL Distribution Point, which causes the Certificate to be checked for revocation each time it's read. Even if you have CRL turned on in IE, VeriSign Code-Signing Certificates aren’t checked.

Microsoft’s update is going to shim in some mechanism which causes some/all Code-Signing Certificates to check some local file/registry key for a CRL, which will (at least initially) contain the details of these Certificates. Assuming this works as advertised, any attempt to trust the mis-issued Certificates should fail.33

Roger Thompson, Chief Technical Officer for Exploit Prevention Labs, explained that the imposters’ motives would determine how bad the results would be from the fraudulent certificates. “If it was someone with a purpose in mind, then six weeks is a long time to do something,” he said. “If the job was to install a sniffer, then there could be a zillion backdoors as a result of it.” Published reports indicated that the failure of authentication occurred due to a flaw in the issuing process at VeriSign: The certificates were issued before receiving verification by email that the official customer contact authorized the certificates. This case was the first detected failure of authentication in over 500,000 certificates issued by VeriSign.34

Some recent cases involving stolen or forged certificates include the following:

- In November 2011, antimalware vendor F-Secure’s Mikko Hypponen reported “finding a piece of malicious software that was cryptographically signed by a forged Adobe certificate originating with Government of Malaysia: Malaysian Agricultural Research and Development Institute ...”35
- In September 2012, Adobe reported that they “… received two malicious utilities that appeared to be digitally signed using a valid Adobe code signing certificate.”36 The company explained, “Sophisticated threat actors use malicious utilities like the signed samples during highly targeted attacks for privilege escalation and lateral movement within an environment following an initial machine compromise.”
- In February 2013, Bit9 Systems revealed that “Due to an operational oversight within Bit9, we failed to install our own product on a handful of computers within our network. As a result, a malicious third party was able to illegally gain temporary access to one of our digital code-signing certificates that they then used to illegitimately sign malware. There is no indication that this was the result of an issue with our product. Our investigation also shows that our product was not compromised.”37

### 17.2.4.4 Certificate Forgery.

Certificate forgery is another hazard. Certificates are not magical; they are merely documented cryptographically signed by a recognized Certification Authority. The cryptographic techniques used to sign certificates
