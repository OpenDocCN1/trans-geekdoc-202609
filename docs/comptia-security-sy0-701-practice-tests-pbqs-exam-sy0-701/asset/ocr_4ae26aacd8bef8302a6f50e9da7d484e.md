Question 391. An organization is planning to deploy a new web application that will be accessible from both the internal network and the internet. The application will communicate exclusively over HTTPS. The security administrator is asked to configure the firewall to allow the necessary traffic. Which of the following should the administrator configure?

+   (A) Allow port 21 and block all others
(B) Allow port 443 and block all others
(C) Allow port 80 and block all others
(D) Allow port 23 and block all others

Explanation 391. Correct Answer: B. Allow port 443 and block all others. HTTPS primarily uses port 443 for secure communication. Thus, allowing port 443 and blocking all others would ensure the secure operation of the web application.

Option A is incorrect. Port 21 is used for FTP (File Transfer Protocol), which is not relevant to HTTPS communication.

Option C is incorrect. While port 80 is used for HTTP, it does not provide the encryption that HTTPS does on port 443.

Option D is incorrect. Port 23 is used for Telnet, which is unrelated to secure web communication.

Question 392. The company’s security administrator observes that there are multiple unauthorized access attempts originating from IP addresses in a specific range. The administrator wants to prevent these IP addresses from accessing the corporate network temporarily. Which of the following firewall configurations would BEST address this requirement?