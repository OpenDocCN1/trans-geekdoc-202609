# 25.2 National Computer Security Center (NCSC) 599

for this kind of thing for themselves, and it was very expensive. The NSA figured that if companies could sell equipment to both the military and the corporate users, even overseas, costs would go down and everyone would benefit. They would no longer endure endorsement as complying with Federal Standard 1027, and CCEP would provide government-endorsed cryptographic equipment [419].

NSA developed a series of cryptographic modules for different purposes. Different algorithms would be used in the modules for different applications, and manufacturers would be able to pull one module and plug in another depending on the customer. There were modules for military use [Type I], modules for "unclassified but sensitive" use [Type II], modules for corporate use [Type III], and modules for export [Type IV]. Table 25.1 summarizes the modules, applications, and names.

This program is still around, but never became popular outside the government. All the modules were tamperproof, all the algorithms were classified, and you had to get your keys from NSA. Corporations never really bought into the idea of using classified algorithms by the government. You'd think the NSA would have learned from this lesson and not bothered with Clipper, Skipjack, and escorted encryption chips.

# 25.2 NATIONAL COMPUTER SECURITY CENTER (NCSC)

The National Computer Security Center, a branch of the NSA, is responsible for the government's trusted computer program. Currently, the center evaluates commercial security products (both hardware and software), sponsors and publishes, develops technical guidelines, and generally provides advice, support, and training.
The NCSC publishes the infamous "Orange Book" [465]. Its actual title is the Department of Defense Trusted Computer System Evaluation Criteria, but that's mouthful to say and the book has an orange cover. The Orange Book attempts to define security requirements, gives computer manufacturers an objective way to measure the security of their systems, and guides them as to what build into their secure products. It focuses on computer security and doesn't really say a lot about cryptography.

The Orange Book defines four broad divisions of security protection. It also defines classes of protection within some of those divisions. They are summarized in Table 25.2.

# Table 25.1
CCEP Modules

| Application | Type I | Type II |
|---|---|---|
| Voice/low-speed Computer | Winster | Edgeshot |
| High-speed data | Tepeache | Bulletproof |
| Next Generation | Forsee | Brushstroke |
| | Countersign I | Countersign II |