# Selecting a Target

One of the first considerations is what to target for your bug-hunting efforts. The best approach is to start searching for bounty programs on registries such as Firebounty.com. The newer the product and the more obscure the interface, the more likely you will find undiscovered issues. Remember, for most programs, only the first report is rewarded. Often sites such as Bugcrowd.com will list any known security issues, so you don’t waste your time on issues that have been reported already. Any effort you give to researching your target and its known issues is time well spent.

# Registering (If Required)

Some programs require you to register or maybe even be vetted by a third party to participate in them. This process is normally simple, provided you don’t mind sending a copy of your identification to a third party such as NetVerify. If this is an issue for you, move on—there are plenty of other targets that do not require this level of registration.

# Understanding the Rules of the Game

Each program will have a set of terms and conditions, and you would do yourself a favor to read them carefully. Often, you will forfeit the right to disclose a vulnerability outside the program if you submit to a bug bounty program. In other words, you will likely have to make your disclosure in coordination with the vendor, and perhaps only if the vendor allows you to disclose. However, sometimes this can be negotiated, because the vendor has an incentive to be reasonable with you as the researcher in order to prevent you from disclosing on your own. In the best-case scenario, the vendor and researcher will reach a win/win situation, whereby the researcher is compensated in a timely manner and the vendor resolves the security issue in a timely manner—in which case the public wins, too.

# Finding Vulnerabilities

Once you have found a target, registered (if required), and understand the terms and conditions, it is time to start finding vulnerabilities. You can use several methods to accomplish this task, as outlined in this book, including fuzzing, code reviews, and static and dynamic security testing of applications. Each researcher will tend to find and follow a process that works best for them, but some basic steps are always necessary:

+   - Enumerate the attack surfaces, including ports and protocols (OSI layers 1–7).
+   - Footprint the application (OSI layer 7).
+   - Assess authentication (OSI layers 5–7).
+   - Assess authorization (OSI layer 7).
+   - Assess validation of input (OSI layers 1–7, depending on the app or device).
+   - Assess encryption (OSI layers 2–7, depending on the app or device).