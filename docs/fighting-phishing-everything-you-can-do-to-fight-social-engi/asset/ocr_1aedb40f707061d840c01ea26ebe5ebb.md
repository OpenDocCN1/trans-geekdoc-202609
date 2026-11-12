instead), it’s easier for a fraudulent site to claim to be something that it’s not or for another malicious node to do man-in-the-middle attacks or eavesdrop on confidential data.

One big caveat to remember is that a large percentage of malicious websites involved in phishing also have valid, legitimate HTTPS digital certificates and connections. According to the Anti-Phishing Working 2021 Q2 Group’s Phishing Activity Trends Report (https://docs.apwg.org/reports/apwg_trends_report_q2_2021.pdf), 82% of phishing websites have valid HTTPS digital certificates (as shown in Figure 8-3).

![](bbox=[0.146, 0.385, 0.892, 0.646])

FIGURE 8-3 Percentage of phishing attacks hosted on valid HTTPS-enabled websites according to the Anti-Phishing Work Group’s 2021 Q2 Group’s Phishing Activity Trends Report.

This is similar to the situation discussed in Chapter 7, “DMARC, SPF, and DKIM.” There we discussed how most phishing domains are protected by DMARC and will have a DMARC status of “pass”. We would rather have phishing websites fail their DMARC checks, but instead, phishers have adopted using DMARC at even greater percentages than non-phishing websites. The same thing happens with HTTPS. Most phishing