
### Initial meeting
Start the process by meeting with upper-level management to find out the scope of what they would like you to do. At this point, you should find out if it is okay to perform all types of testing, such as denial of service attacks, buffer overflow attacks, and password attacks (to name a few). Also, at this point you should reiterate that you cannot guarantee that denial of service will not happen.

### Draft legal documents
After the initial meeting, see a lawyer and have a legal document drafted stating that you are allowed to do the penetration test. Be sure to have the document signed by an authorized representative of the organization you are doing the penetration test for.

### Create a pentest plan
Once you have the document signed, plan the types of attacks or testing you will perform. The purpose of building a plan is so that you are disciplined and follow a methodology in your approach and don’t just have a field day hacking someone’s network.

### Test the pentest plan
Test the tools you will use to perform the different types of attacks to ensure they work and to see if they will cause a denial of service when executed.

### Perform a penetration test
At this point you are at the customer’s site performing the penetration test and following your plan. Be sure to test password cracking, wireless cracking, and buffer overflow attacks. Test physical security elements and social engineering attacks against the organization as well. Be sure to document everything you do, including the start time and end time of each step.

### Create a report on findings
Once the test is complete, create a report of your findings. You do not have to include your log of all activities, but be sure to have it handy in case you have to refer to it. You should include screenshots of successful and failed attacks on the systems along with recommendations on how to improve security.

### Present report results
In this phase, you will meet with upper-level management again to report your findings and give them a copy of the report. Ensure that you have the customer sign off on a completed assessment.

### Destroy any copies of the report
As a final step, ensure that you do not have additional copies of the assessment in either printed form or electronic form.

## Performing a Vulnerability Assessment

Another type of security test you can perform instead of a penetration test is a vulnerability assessment. A vulnerability assessment is considered a passive type of assessment because you are not actually simulating attacks against the system. With the vulnerability assessment, you are looking to identify any weaknesses in the configuration of the network and its systems and are not interested in actually testing those weaknesses to see if you can compromise the systems.

When management asks you to assess security but are uncomfortable with the fact that you will be running hacking tools against the systems, then you should do a vulnerability assessment. The primary benefit is that it is a safe type of assessment with no risk of creating a denial of service on the systems.

### Performing a Manual Assessment

When performing a vulnerability assessment, I recommend first doing a manual assessment of the network and its systems. With the manual assessment, you are essentially performing a configuration assessment and verifying the configuration of the network, clients, devices, and servers. In this manual assessment you will look to ensure that best practices are being followed, such as ensuring each system has a password policy and that virus protection software is being used. Keep in mind that on a big network this could take a long time, so it is critical that you have a checklist to go by to keep you on track.

### Performing an Automated Assessment

When you perform a vulnerability assessment, you are most likely to use vulnerability assessment software such as `LANguard` or `Nessus`. These are two of the leading products for vulnerability assessment, and they definitely take a lot of the work away from you! For this discussion, I will use `GFI LANguard` to demonstrate the usefulness of a vulnerability scanner.

#### Performing the Scan
When using a vulnerability scanner such as `Nessus` or `LANguard`, the first thing to understand is that these tools help automate the process of performing a vulnerability scan by scanning multiple systems and comparing the system configurations to a vulnerability database.

When performing your vulnerability scan, I recommend that you perform the scan twice: once as a null scan (you have not authenticated to the network because you do not know the username and password of an account), and the other as a scan with an administrative account. The purpose of performing the scan twice is to ensure that the first scan lets you understand what a “nobody” would see about your network if they could physically connect to your network, and the second scan allows you to connect to all systems with an administrative account so that you can get a full assessment of the configuration. The following exercise will walk you through how to perform a scan with `Nessus`.

#### EXERCISE 20-4

![Images](video.jpg)

#### Performing a Vulnerability Scan with Nessus

In this exercise, you download, install, and run a vulnerability scanner known as `Nessus` on your Kali Linux system. The vulnerability scanner will identify vulnerabilities that exist and give detailed information about each one. Ensure you have your Windows Server and Kali Linux VMs running for this exercise.

1. On the Kali Linux VM, launch a browser and navigate to <https://www.tenable.com/products/nessus>.
2. Choose to download the AMD64 Debian/Kali Linux edition.
3. Launch a terminal session and run the following commands to view the download:

![Image](p0806-01.jpg)

4. To install `Nessus`, use the following command:

![Image](p0807-01.jpg)

where `#` represents the version number you downloaded

5. After the installation you must start the `Nessus` service with the following command:

![Image](p0807-02.jpg)

6. To use `Nessus`, switch to the web browser and type the following URL:

![Image](p0807-03.jpg)

7. Choose `Nessus Essentials` as the edition to use (it is the free version that allows you to scan up to 16 IP addresses).
8. Enter your details and then choose E-mail.
9. Check your e-mail for an activation code and then enter it into `Nessus`.
10. Create a `Nessus` user account with the following details:

![Image](p0807-04.jpg)

11. The plugins will then download and compile on the system. Each plugin is used to check for a different type of vulnerability. This step will take some time.
12. Once the plugins download and compile, you are placed at the `Nessus` welcome screen. Choose Close.
13. Create a new Advanced Scan that scans the IP address of your Windows Server.
14. Ensure that all plugins are enabled. Each plugin checks for a specific type of vulnerability during the scan. Note the Windows plugins at the bottom of the list.
15. Save the scan settings.
16. Looking at the scan list, start the newly created scan.
17. The scan will take some time, but once it completes, review the results to identify the vulnerabilities with the system.

#### Interpreting the Results
Once you have completed the vulnerability scan, it is critical that you spend some time reviewing the results to come up with a diagnosis of whether the systems are secure. If the systems are not secure, you will need to make recommendations on what can be done to improve the security. The following list outlines some of the possible actions to take to improve the security:
