...[/content] wrapper.

We need to ensure we keep all information, no summarization.

Now we need to decide how to format headings: Use ## for level 1, ### for level 2. The OCR headings: "# Exercise 13.2: **Criminal Records Checks**" is level 1, so "## Exercise 13.2: Criminal Records Checks". Also "# Exercise 13.3: Checking Court Cases" => "## Exercise 13.3: Checking Court Cases". "# Exercise 13.4: Finding Business Information on Usenet" => "## Exercise 13.4: Finding Business Information on Usenet". "# Exercise 13.5: Blocking Information" => "## Exercise 13.5: Blocking Information". "# Chapter 14. **Introduction to Forensics**" => "## Chapter 14: Introduction to Forensics". "# *Chapter Objectives*" => "## Chapter Objectives". "# Introduction" => "## Introduction". Also maybe "## Introduction to Forensics" is a level 1 heading, but there is also "## Introduction" which is also level 1. That's fine.

List items: The OCR list items are preceded by "+   1." etc. We'll convert to "- 1." but maybe we need to keep numbering? Not required but we can keep numbers after dash. Eg "- 1. Using sources listed..." That's okay.

Also there are list items under Chapter Objectives: "+   - Understand basic forensics principles". That's already using "-". We'll keep as "- Understand basic forensics principles". Also there is a bullet with "-   - Understand basic forensics principles"? Actually it's "+   - Understand basic forensics principles". That's weird: plus then dash. Probably it's a formatting artifact; we should output "- Understand basic forensics principles". Also "+   - Make a forensic copy of a drive" => "- Make a forensic copy of a drive". "+   - Use basic forensics tools" => "- Use basic forensics tools".

Now we need to merge paragraphs across pages.

Let's construct the final text:

Start with the first paragraph after page 470: "Did you get too little information or too much information? Were you able to determine the correct, current number?" That's a paragraph.

Then heading "## Exercise 13.2: Criminal Records Checks". Then list items:

- 1. Using sources listed in this chapter or other websites, look for criminal background information about John Doe. Start with the state John currently resides in, and then check other states, particularly those that might have shown up with John’s name in Exercise 13.1.

- 2. Expand your search to check for federal crimes as well.

Then heading "## Exercise 13.3: Checking Court Cases". List items:

- 1. Search court records for any court cases for Jane Doe’s business.

- 2. Check state licensing agency websites, if applicable, for any history or complaints on John’s business.

Then heading "## Exercise 13.4: Finding Business Information on Usenet". List items:

- 1. Access Usenet.

- 2. Search bulletin boards and other groups that Jane Doe may have posted to in connection with her business.

Then question paragraph: "Were you able to find out more about Jane’s business through her postings to a Usenet group?" That's a paragraph (maybe separate). It could be part of same paragraph as previous? It's a separate sentence, but we can treat as its own paragraph.

Then heading "## Exercise 13.5: Blocking Information". Then paragraph: "This chapter illustrated the many ways you can access information about someone and pointed out the potential hazards of having too much personal information available on the Internet. So, what can you do to prevent unscrupulous individuals from finding out too much". Then next page continues: "about you? Check the primary websites listed in this chapter (Yahoo! and Google) to see if they provide any means to block your information from being distributed. Are there any other means of blocking access to your personal information?" So we need to combine these into one paragraph: "This chapter illustrated the many ways you can access information about someone and pointed out the potential hazards of having too much personal information available on the Internet. So, what can you do to prevent unscrupulous individuals from finding out too much about you? Check the primary websites listed in this chapter (Yahoo! and Google) to see if they provide any means to block your information from being distributed. Are there any other means of blocking access to your personal information?" That's a paragraph.

Then next paragraph: "Using all of the web resources in this chapter and any others you come across, do a complete investigation of Jane Doe. Try to determine her address, phone number, occupation, age, and any criminal history. You might even check Usenet postings and find out clues as to Jane's hobbies and personal interests. Create a brief report on Jane based on your findings."

Next paragraph: "Using all of the web resources in this chapter and any others you come across, do a complete investigation of John Doe's business. How long has he been in business? Are there any complaints about the business with any regulatory agency? Any complaints on Usenet boards? Any business relationships? Any past court proceedings? Write a report discussing your analysis of this business based on your findings."

Next paragraph: "Write an essay discussing the ethics of online investigations. Do you feel these investigations are an invasion of privacy? Why or why not? If you do feel they are an invasion of privacy, what do you think can be done about it? Are there problems with getting inaccurate information?"

Now page 472 content: "Henry Rice, the owner and CEO of a small company, has been conducting a search for a new human resource administrator. After many rounds of interviews, he has narrowed his search down to two individuals whom he feels are the best candidates. Each has very similar qualifications, so Henry's decision may very well be based on the information he finds when he checks their references and performs a background check."

Then heading "## Chapter 14: Introduction to Forensics". Then "## Chapter Objectives". Then "**After reading this chapter and completing the exercises, you will be able to do the following:**" maybe we need to keep as text, not as heading. But it's a line; we can keep as is, maybe not as heading. However spec: identify titles (## for level 1, ### for level 2). This line is not a heading; it's just text. So we keep as plain text.

Then list items:

- Understand basic forensics principles

- Make a forensic copy of a drive

- Use basic forensics tools

Then heading "## Introduction". Then paragraph: "In the preceding 13 chapters, you have been introduced to a variety of security topics: from concepts like the CIA triangle, to attacks such as session hijacking, to counter measures like IDS and honey pots. In this chapter, we are going to cover the basics of computer forensics. This is a very important topic for anyone involved in computer security or network administration. It is frequently the case that the first responder to a computer crime is the network administrator, not a law enforcement officer. And if you fail to handle the evidence properly, you may render it unusable in a court and ruin any chances of convicting the perpetrator."

Next paragraph: "Computer forensics is a comparatively new field. Widespread use of computers dates back to the 1970s and widespread computer crime to the 1990s. The field of computer forensics has evolved only in the past 20 to 25 years. The field of computer forensics, now often called cyber forensics, attempts to apply forensic science to computer devices."

Next: "CERT defines computer forensics in this manner:" then blockquote. We need to convert blockquote to maybe a separate paragraph? The blockquote content is:

"If you manage or administer information systems and networks, you should understand computer forensics. Forensics is the process of using scientific knowledge for collecting, analyzing, and presenting evidence to the courts. (The word *forensics* means “to bring to the court.”) Forensics deals primarily with the recovery and analysis of latent evidence. Latent evidence can take many forms, from fingerprints left on a window to DNA evidence recovered from blood stains to the files on a hard drive."

We can keep as a paragraph (maybe with line breaks). Since it's a blockquote, but we can just include as paragraph.

Next paragraph: "The goal of cyber forensics is to examine computer devices (laptops, servers, cell phones, tablets, and so on) using scientific methods to extract evidence in such a way that such evidence can be presented in a court. Now, there are certainly times when you will use forensics in scenarios that will never go to court. But the techniques were designed to satisfy the evidentiary requirements of courts."

Next paragraph: "It is important to keep in mind that a few jurisdictions have passed laws requiring that in order to extract the evidence, the investigator must be either a law enforcement officer or a licensed private investigator. This is a controversial law, given that normally private investigator training and licensing does not include computer forensics training. You should check with specifics in your state. However, many of those states will allow you to forensically examine a computer if you have the permission of the owner or if someone who is licensed seized the evidence. So this would not prohibit you from forensically examining computers in your company."

Next paragraph: "The purpose of this chapter is to give you a general introduction to the field of forensics. Clearly, each topic discussed in this chapter could be investigated in more depth."

Now we need to ensure we have blank lines separating paragraphs. Also need to ensure list items are preceded by "-". Also need to ensure headings are preceded by "##". Also need to ensure we don't keep page markers.

Now we need to check for any OCR errors that need correction:

- In "the word *forensics* means “to bring to the court.”" maybe the curly quotes are fine.

- "the evidence can be presented in a court." fine.

- "the first responder to a computer crime is the network administrator, not a law enforcement officer." fine.

- "the field of computer forensics, now often called cyber forensics" fine.

- "the evidence can be presented in a court." fine.

- "the investigator must be either a law enforcement officer or a licensed private investigator." fine.

- "the purpose of this chapter is to give you a general introduction to the field of forensics." fine.

Potential errors: "the many ways you can access information about someone and pointed out the potential hazards of having too much personal information available on the Internet." maybe "the many ways you can access information about someone and pointed out the potential hazards of having too much personal information available on the Internet." fine.

- "Check the primary websites listed in this chapter (Yahoo! and Google) to see if they provide any means to block your information from being distributed." fine.

- "Are there any other means of blocking access to your personal information?" fine.

- "Using all of the web resources in this chapter and any others you come across, do a complete investigation of Jane Doe." fine.

- "do a complete investigation of John Doe's business." fine.

- "Write an essay discussing the ethics of online investigations." fine.

- "Write a brief essay outlining the steps Henry should take in conducting his research." fine.

Now we need to ensure we convert the list items from "+   1." to "- 1." Also ensure we keep numbers.

Let's rewrite list items:

Exercise 13.2 list:

- 1. Using sources listed in this chapter or other websites, look for criminal background information about John Doe. Start with the state John currently resides in, and then check other states, particularly those that might have shown up with John’s name in Exercise 13.1.

- 2. Expand your search to check for federal crimes as well.

Exercise 13.3 list:

- 1. Search court records for any court cases for Jane Doe’s business.

- 2. Check state licensing agency websites, if applicable, for any history or complaints on John’s business.

Exercise 13.4 list:

- 1. Access Usenet.

- 2. Search bulletin boards and other groups that Jane Doe may have posted to in connection with her business.

Exercise 13.5 list: none (just paragraph).

Now list items under Chapter Objectives:

- Understand basic forensics principles

- Make a forensic copy of a drive

- Use basic forensics tools

Now we need to ensure we have blank lines separating paragraphs. Also ensure we don't have extra spaces.

Now we need to output final content inside [content]...[/content].

Let's craft final text:

[content]
Did you get too little information or too much information? Were you able to determine the correct, current number?

## Exercise 13.2: Criminal Records Checks
- 1. Using sources listed in this chapter or other websites, look for criminal background information about John Doe. Start with the state John currently resides in, and then check other states, particularly those that might have shown up with John’s name in Exercise 13.1.
- 2. Expand your search to check for federal crimes as well.

## Exercise 13.3: Checking Court Cases
- 1. Search court records for any court cases for Jane Doe’s business.
- 2. Check state licensing agency websites, if applicable, for any history or complaints on John’s business.

## Exercise 13.4: Finding Business Information on Usenet
- 1. Access Usenet.
- 2. Search bulletin boards and other groups that Jane Doe may have posted to in connection with her business.

Were you able to find out more about Jane’s business through her postings to a Usenet group?

## Exercise 13.5: Blocking Information
This chapter illustrated the many ways you can access information about someone and pointed out the potential hazards of having too much personal information available on the Internet. So, what can you do to prevent unscrupulous individuals from finding out too much about you? Check the primary websites listed in this chapter (Yahoo! and Google) to see if they provide any means to block your information from being distributed. Are there any other means of blocking access to your personal information?

Using all of the web resources in this chapter and any others you come across, do a complete investigation of Jane Doe. Try to determine her address, phone number, occupation, age, and any criminal history. You might even check Usenet postings and find out clues as to Jane's hobbies and personal interests. Create a brief report on Jane based on your findings.

Using all of the web resources in this chapter and any others you come across, do a complete investigation of John Doe's business. How long has he been in business? Are there any complaints about the business with any regulatory agency? Any complaints on Usenet boards? Any business relationships? Any past court proceedings? Write a report discussing your analysis of this business based on your findings.

Write an essay discussing the ethics of online investigations. Do you feel these investigations are an invasion of privacy? Why or why not? If you do feel they are an invasion of privacy, what do you think can be done about it? Are there problems with getting inaccurate information?

Henry Rice, the owner and CEO of a small company, has been conducting a search for a new human resource administrator. After many rounds of interviews, he has narrowed his search down to two individuals whom he feels are the best candidates. Each has very similar qualifications, so Henry's decision may very well be based on the information he finds when he checks their references and performs a background check.

## Chapter 14: Introduction to Forensics
## Chapter Objectives
**After reading this chapter and completing the exercises, you will be able to do the following:**
- Understand basic forensics principles
- Make a forensic copy of a drive
- Use basic forensics tools

## Introduction
In the preceding 13 chapters, you have been introduced to a variety of security topics: from concepts like the CIA triangle, to attacks such as session hijacking, to counter measures like IDS and honey pots. In this chapter, we are going to cover the basics of computer forensics. This is a very important topic for anyone involved in computer security or network administration. It is frequently the case that the first responder to a computer crime is the network administrator, not a law enforcement officer. And if you fail to handle the evidence properly, you may render it unusable in a court and ruin any chances of convicting the perpetrator.

Computer forensics is a comparatively new field. Widespread use of computers dates back to the 1970s and widespread computer crime to the 1990s. The field of computer forensics has evolved only in the past 20 to 25 years. The field of computer forensics, now often called cyber forensics, attempts to apply forensic science to computer devices.

CERT defines computer forensics in this manner:
If you manage or administer information systems and networks, you should understand computer forensics. Forensics is the process of using scientific knowledge for collecting, analyzing, and presenting evidence to the courts. (The word *forensics* means “to bring to the court.”) Forensics deals primarily with the recovery and analysis of latent evidence. Latent evidence can take many forms, from fingerprints left on a window to DNA evidence recovered from blood stains to the files on a hard drive.

The goal of cyber forensics is to examine computer devices (laptops, servers, cell phones, tablets, and so on) using scientific methods to extract evidence in such a way that such evidence can be presented in a court. Now, there are certainly times when you will use forensics in scenarios that will never go to court. But the techniques were designed to satisfy the evidentiary requirements of courts.

It is important to keep in mind that a few jurisdictions have passed laws requiring that in order to extract the evidence, the investigator must be either a law enforcement officer or a licensed private investigator. This is a controversial law, given that normally private investigator training and licensing does not include computer forensics training. You should check with specifics in your state. However, many of those states will allow you to forensically examine a computer if you have the permission of the owner or if someone who is licensed seized the evidence. So this would not prohibit you from forensically examining computers in your company.

The purpose of this chapter is to give you a general introduction to the field of forensics. Clearly, each topic discussed in this chapter could be investigated in more depth.
