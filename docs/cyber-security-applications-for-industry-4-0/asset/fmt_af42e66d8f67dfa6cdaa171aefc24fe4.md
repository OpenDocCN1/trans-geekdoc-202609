
## 1. IP Spoofing
Every device has a unique IP Address. By spoofing one’s IP address, the attacker makes the victim think that they are interacting with a website which isn’t the case. Thus, it enables the hacker to get all the user information of the victim.

## 2. DNS Spoofing
Domain Name Server spoofing is a method that forces the user to use a fake website instead of the original. This allows them to divert traffic from the actual site in order to hold user login credentials.

## 3. HTTPS Spoofing
Every URL in the Internet starts with HTTP. But we must ensure that we always use secure websites which are usually identified with the website starting with HTTPS where S means secured. The attacker usually fools the victims by redirecting their browser to an unsecured website. This enables them to monitor the user’s interactions with that webpage so that they could steal the personal information which they are sharing.

## 4. SSL Hijacking
Secure Sockets Layer (SSL) is a protocol that establishes encrypted links between a web server and a browser. This ensures that the data shared with the server is secure.
In SSL hijacking, the attacker successfully captures all data passing between the target computer and the server through another computer and secure server.

## 5. Email Hijacking
Email accounts of banks and various other financial institutions are targeted so that attackers can gain access to and monitor transactions between the organization and its customers. The bank’s email address has shovels to send its instructions to customers. Therefore, the attackers impersonate the bank and assured customers to follow their orders rather than the bank. Hence, the customers are fooled to deposit their money to the fraudsters.

## 6. Wi-Fi Eavesdropping
Wi-Fi connections are set by attackers with real audible names. When a user connects to the attacker’s Wi-Fi, the user’s online activity can be monitored and it is possible to obtain login credentials, credit card details, and other sensitive information. To avoid such dangers, we should not use public Wi-Fi.

## 7. Stealing Browser Cookies
A browser cookie is a small piece of information stored by a website on a personal computer.
Because cookies store data from personal browsers, attackers can gain easy access to passwords, addresses, and other sensitive information. Therefore, attackers often steal these browser cookies.
Some of the examples of Man in the Middle attacks are Babington Plot in 1586, Cracking the Enigma Code by British Intelligence in the Second World War, Edward Snowden exposing NSA in 2013, Lenovo using Superfish in 2014, and Lupton Couple incident in 2015.

### Prevention steps
The prevention steps that can be followed are:
* Disable your devices to connect automatically to Wi-Fi networks. Make sure you only use trusted Wi-Fi networks.
* The access points need to be encrypted and secured.
* Use VPN to secure your traffic while connecting to an unknown or public Wi-Fi network.
* Avoid sharing sensitive information with an unsecured URL (secured ones begin with https://).
* Always enable Two-Factor Authentication to your accounts.
* Regularly update the OS so that attackers don’t exploit the weaknesses of an outdated system OS.
* Installing a trusted antivirus software is a must, followed by regular weekly scans.
* Beware of phishing attempts in your emails and never log in to a link of a mail if it seems suspicious.
* Wi-Fi network should be secured and always use strong and unique login credentials instead of the default ones.

### 1.3.4.2 2015 Lupton Couple Incident
In February 2015, Paul and Ann Lupton a couple from Britain sold their flat which they had earlier bought for their daughter [[35](#ch1.xhtml#ref1_35)]. After all the negotiations, they received an email from their Solicitor on February 27 which was two days before the completion date, requesting their bank account details so as to transfer the amount of £340,000 into their account.
This entire transaction and fraud took place in Barclays Bank Account. As a reply to Solicitor’s mail, Mr. Lupton sent his Sort Code and bank’s Account number. The mail was intercepted in the middle by the hackers. They used a sophisticated tool that examines numerous emails to identify the ones which shall contain valuable information. The attackers posed as Mr. Lupton and sent an email to the Solicitor to omit the previously sent account and instead pay in their (fraud) account. This was an email eavesdropping/email hijacking MitM attack. Thus, the solicitor sent the balance amount after deducting his consultation charges. The fraudulent account received £333,000.
After a few days, when the Lupton Family enquired their solicitor about their payment which was due, they came to know about the fraud. Immediately, the fraud was brought under the notice of both Barclays Bank and the police. This event highlighted the lack of resources that firms have to safeguard their client’s money. The sensitive and confidential information are under threat in emails as well. On hearing about this incident, various Government security service firms stated that this case was a wake-up call of how sophisticated the hackers have become these days. The Solicitors Regulation Authority (SRA) had made a verdict and warned that financial firms are responsible for protecting their customers’ finances and should be compensated if their funds are misappropriated or withdrawn from the customer’s account. Although they can’t force the firms to compensate the victims.
After this event, Barclays froze Mr. Lupton’s account and initially returned £271,000 to them, although they tried to defend themselves and blamed the sophistication of the fraud. And after eight months, their PI insurer (Perry Hay & Co) paid the balance amount and reimbursed the victim (The Luptons).
Although detecting an eavesdropping attack is challenging, the following steps help to reduce the risk significantly [[37](#ch1.xhtml#ref1_37)]:
* **Encryption**: Emails, networks, and communications, and data at rest, in use, and in motion need to be encrypted. Attackers would need an encryption key to decrypt the files. Using a 256-bit which is also known as military-grade encryption is ideal.
* **Authentication**: In order to prevent IP spoofing, we need to authenticate the incoming packets. Using standards and protocols that provide authentication is also suggested.
* **Network Monitoring**: Deploying an intrusion prevention system is a must so as to constantly monitor traffic and identify abnormal activity.
* **Cybersecurity Awareness**: Basic knowledge of cybersecurity needs to be taught to the users. This helps them to tackle the situation better. Using strong passwords in systems and Wi-Fi networks and avoiding public networks are some known facts. Encourage the use of VPNs and Firewalls.
* **Network Segmentation**: Segmenting the network ensures that the data can’t be accessed and reached by the hacker. The separate segment partition ensures that traffic can’t flow from one segment to the other.

### 1.3.4.3 2014 Samsung Smart Fridge Man in the Middle Exposure
In April of 2014, Samsung took a second shot at making a smart fridge named Samsung RF28HMELBSR/AA Refrigerator which was priced at $3599 with an 8-inch LCD screen, inbuilt Wi-Fi, and features like phone mirroring, “Kitchen TV”, wherein users would be able to connect the Fridge to the antenna’s signals and enjoy the broadcast from their kitchen, as well as “kitchen calling” wherein users would be able to make calls directly from the smart fridge. The fridge also has the capability to display the calendar and also the news. However, with the plethora of features that the fridge brought, it also brought with it some vulnerabilities which when exploited could potentially be dangerous.
