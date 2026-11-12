
## Configuring DMARC, SPF, and DKIM

Creating the DNS records, enabling, and configuring DMARC, SPF, and DKIM is beyond the scope of this book. It would take many dozens of additional pages to cover configuration options. There are dozens of different configuration options in each protocol and it is easy to make a mistake. Enabling each of them varies depending on the involved email and DNS service. But if you do a little Internet searching on DMARC, SPF, and DKIM, you will find hundreds of pages about these protocols and how to configure and enable them.

There are many open-source tools related to DMARC, SPF, and DKIM. Most are related to DMARC data collection and reporting, graphically showing DMARC report data. You can also avail yourself of any of the commercial companies that will handle DMARC, SPF, and DKIM for you. Many organizations find it far easier to let someone else handle it for them. There are many good commercial services, including the following:

- EasyDMARC
- Dmarcian
- Agari
- Validity
- Dmarcly

KnowBe4 is an investor in EasyDMARC.

In general, if you use a commercial service, you’re going to have a better DMARC experience and outcome.

If you are interested in learning more about DMARC, SPF, and DKIM and how to enable and configure them, consider watching my related one-hour webinar: https://info.knowbe4.com/implementing-dmarc.

## Putting It All Together

DMARC, SPF, and DKIM work in conjunction with each other. When all are enabled on the sender's side, a receiver can validate multiple pieces of information. SPF will validate the sender's 5321 email address domain. DKIM will allow the receiver to verify the domain indicated in the sender's DKIM signature (i.e., the d= variable) and that the email was unadulterated from the time it was sent to the time it was received. DMARC will verify the alignment of the DKIM signature to the 5322 email address domain. Each of these services will have its own PASS or FAIL (or other designation). A FAIL from any of them will apply DMARC's policy instruction (indicated in the p= variable) of how the receiver should handle failed emails (i.e., None, Quarantine, or Reject).

From a path flow perspective, when a DMARC-enabled email arrives at a receiver's email server/service, that email server/service will first apply all its normal cybersecurity checks (e.g., anti-phishing, anti-spam, anti-malware, content filtering, etc.) and then start to apply the DMARC checks (if enabled). If DMARC is determined to have been enabled (as indicated in the email headers), the receiving email server/service will connect to the sender's DNS server and download the DMARC, SPF, and DKIM DNS records. It will then use those DNS records to do the involved validation and update the email headers as determined by the validation outcomes. Based on the DMARC, SPF, and DKIM checks, the email may or may not be sent to the recipient's email inbox or quarantine folder. The email can also be rejected at the email server/service and never make it to the final recipient's email client. This process is graphically summarized in Figure 7-18.

![](img/49fb1c0c9ac2e62e5db4a36fa9f8b591_199_0.png)

FIGURE 7-18 How DMARC, SPF, and DKIM validation checks flow.

## DMARC Configuration Checking

You can check your organization’s own domains and those of other entities for DMARC, SPF, and DKIM configurations. There are checkers all over the Internet. Here is one by Dmarcian, a DMARC company created by one of the main co-founders of DMARC: https://dmarcian.com/dmarc-tools.

Figure 7-19 shows the results of running Dmarcian’s DMARC checking tool against knowbe4.com.

| DMARC | SPF | DKIM |
| --- | --- | --- |
| ! DMARC Your domain has a valid DMARC record and it is set to p=quarantine. To fully take advantage of DMARC, the policy should be set to p=reject. + Details | ✓ SPF Your domain has a valid SPF record and the policy is sufficiently strict. - Details v=spf1 include.mailersend.net4life.com include_spf.google.com include.mail.zendesk.com include.stagpcustomer.com ms-spf.intercom.net ip4:23.210.109.197 ip4:52.49.201.246 ip4:52.49.235.189 ip4:54.172.84.960 ip4:147.160.167.70/24 ip4:169.235.256.71 ip4:168.235.226.72 ip4:168.235.226.73 ip4:168.235.226.74 ip4:198.235.233.211 ip4:168.235.233.212 ip4:168.235.233.213 ip4:192.254.121.246 ip4:167.89.63.53 mx=a:wtxa.net include:_netblocks.salesforce.com -all | ✓ DKIM Your DKIM record is valid. + Details |

FIGURE 7-19 Results of running the DMARC checking tool against knowbe4.com.

Depending on which DMARC checker you run, you may get warnings or indications of misconfigurations, even if that organization doesn’t truly have something to worry about. For example, Figure 7-19 shows KnowBe4’s DMARC record as having a warning, but it is just because our DMARC record is set to quarantine versus reject, which is what KnowBe4 wants.

## How to Verify DMARC Checks

There are two main ways to verify DMARC (i.e., DMARC, SPF, and DKIM) checks. One way is to just let the mail agents do their jobs. When DMARC is enabled on sending and receiving agents, the agents will verify the various enabled DMARC checks and handle them accordingly. Most users don’t have to do anything. It’s handled for them.

The second way, and I believe the more interesting way, is to manually investigate individual emails when it’s desired or needed. You can see the various DMARC status outcomes by searching in the email header for dmarc=, spf=, and dkim=. How you get to an email header depends on the email client you are using. In Microsoft Outlook, for example, you open the individual email, then choose File, Properties, and look in the Internet Headers field. You can scroll through the header information shown there, although I prefer to copy all the header information (using Ctrl-A and then Ctrl-C) to Microsoft Notepad (using Ctrl-V) so I can more easily see and find information. In Gmail, you can open an email, click on the three “More” dots and choose Show Original. As shown in Figure 7-20, Gmail is nice enough to show you the DMARC outcome statuses without having to wade through the entire email header (although the entire header is also shown below the summary).

| Original Message |
| --- |
| Message ID | <181a17390d6213 (b7af2150-b971-49d4-e705-5cabba9c01b0)@outlook.com> |
| Created at | Fri, Sep 8, 2023 at 6:25 AM (Delivered after 2 seconds) |
| From: | Stu Sjouwerman <sjouwerman@knowbe4.com> |
| To: | rogerg@knowbe4.com |
| Subject: | Hacking Your Digital Identity: How Cybercriminals Can and Will Get Around Your Authentication Methods |
| SPF: | PASS with IP 54.174.60.48 Learn more |
| DKIM: | 'PASS' with domain knowbe4.com Learn more |
| DMARC: | 'PASS' Learn more |

FIGURE 7-20 An example of DMARC outcomes displayed by Gmail.

There are a bunch of email header parsers on the Internet that will analyze and break down email headers, which can be very “noisy”, for you. Just type in “email header parser” into any Internet search engine, although one of my favorites is: https://mha.azurewebsites.net. You'll have to copy the email header into them, and of course, providing that type of information to any third party invites potential privacy risks.

When I'm in heavy forensics troubleshooting mode, I prefer to review the whole header (which we will cover in more detail in Chapter 15, “Forensically Examining Emails”) because it contains lots of other useful information. But Gmail's displayed version is easier and quicker to read and often more accurate for beginning DMARC investigators. Personally, I often use https://mha.azurewebsites.net for quick checks, because it works with any email client, and I use multiple email clients.

## How to Use DMARC

It's important to realize that a DMARC success or failure doesn't mean a particular email is or isn't a malicious email. DMARC informs you (or your agent on your behalf) about whether the SPF and DKIM authentication mechanisms are successfully passing and aligning with the relevant email domains (the 5321. MailFrom matching with 5322.From address domain for SPF and the d= domain matching with the 5322.From address domain for DKIM). No more, no less. Still, this is important information that can be used to help determine if an email is malicious or not.

Many to most phishing emails pass all DMARC checks. This is because spammers and phishers realized that if they didn't enable and use DMARC, their emails would more than likely end up in quarantine folders most of the time, drastically undermining their conversion rates and numbers of victims. So, phishers aggressively adopted DMARC, and most phishing emails will pass all DMARC checks. Although, most of the time, the phishers have their DMARC policy set to None, so that even failures won't get quarantined or rejected.
