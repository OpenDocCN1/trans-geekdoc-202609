Outlook, by default, will block active content from untrusted senders and sites, but will allow automatic downloading if the sender is in the “Safe Senders” or “Safe Recipients” lists or the originating domain is in the “Trusted Zone.”

It can’t hurt to be warned before an email client downloads content when a user is editing, forwarding, or replying to an email (as the unchecked security setting in Figure 9-5 displays). Most email clients will automatically download content if the user is replying to or forwarding an email. The assumption is that if the user is doing those activities, they trust the email and its included content. This is not always true. For example, I often forward suspicious emails to a special email account I have set up on my forensics virtual machine to inspect it in a safer, more isolated environment. If I didn’t disable content when forwarding emails, simply forwarding the email there could download content, which is not something I would want to do. So, I would want to intentionally enable the “Warn me before downloading content when editing, forwarding, or replying to email” security option.

# Firewalls

Although firewalls do not stop most of today’s threats, they can stop a minority of threats and some network-based social engineering, and for that alone, they should be enabled by default on networks and endpoints. Host-based firewalls should be enabled on all client endpoints with deny-by-default rules.

# Phishing-Resistant MFA

As covered in Chapter 8, all users should enable phishing-resistant multifactor authentication (MFA) whenever possible to protect sensitive data and systems. About half of social