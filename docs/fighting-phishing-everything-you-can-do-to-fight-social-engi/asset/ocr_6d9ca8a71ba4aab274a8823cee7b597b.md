# # Malicious Downloads

Currently, about a quarter of all phishing messages include a malicious download (or a link to a malicious download) that the scammer wants to trick the user into executing or opening. Malicious files can come in over a hundred different file formats. According to VirusTotal, these are some of their findings regarding the types of these malicious files (https://assets.virustotal.com/reports/2023emerging.pdf):

+   - Often, the scammer is trying to get the user to run a Java-Script file, which contains malicious instructions.
+   - About 20% of malicious files are compressed (e.g., .zip, .arc, etc.).
+   - About 45% of malicious file attachments are .html files.
+   - About 10% of malicious downloads are PDF files with harmful embedded instructions or links.
+   - Microsoft Word and Excel files are decreasing in popularity since Microsoft automatically blocked macro execution a few years ago.
+   - ISO and Microsoft OneNote file formats are increasing in hacker popularity in 2023.

Many malicious files are often password-protected or locked so that anti-malware detectors cannot open them. In those cases, usually, the password or unlock code is part of the phishing message text so that the file gets past malware inspectors but is still able to be opened by potential victims. Locked or unlocked, sadly, a large percentage of malicious downloads are not detected by any antivirus scanner as malicious and can readily exploit the end user if opened.

Links and files are often programmatically chained together so that when the user opens the first one, they get a second, which