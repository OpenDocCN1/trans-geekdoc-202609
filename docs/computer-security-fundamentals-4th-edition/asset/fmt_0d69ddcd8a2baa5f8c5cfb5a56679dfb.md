
# Chapter 9. Computer Security Technology

## Chapter Objectives

After reading this chapter and completing the exercises, you will be able to do the following:

*   Evaluate the effectiveness of a scanner based on how it works
*   Choose the best type of firewall for a given organization
*   Understand antispyware methods
*   Employ intrusion detection systems to detect problems on your system
*   Understand honey pots

## Introduction

Throughout this book, various aspects of computer security have been discussed. At this point in your studies, you should have a good idea of what the real dangers are and what adequate security measures include, as well as a basic understanding of the various forms of computer attacks. However, if you are striving to secure a network, you will need more technical details on the various security devices and software you might choose to employ. This chapter reviews these items and provides enough detail to allow you to make intelligent decisions about which types of products you will use.

Most of the devices described in this chapter have been mentioned and briefly described in the preceding chapters. The intent of this chapter is to delve more deeply into details of how these devices work. This information is of particular value to those who intend to eventually enter the computer security profession. Simply having a theoretical knowledge of computer security is inadequate. You must have some practical skills. This chapter will be a good starting point for gaining those skills, and the exercises at the end of the chapter will give you a chance to practice setting up and evaluating various types of firewalls, intrusion detection systems (IDSs), and antivirus applications.

## Virus Scanners

A *virus scanner* is essentially software that tries to prevent a virus from infecting a system. This fact is probably abundantly obvious to most readers. Knowing how a virus scanner works, however, is another matter. This topic was discussed briefly in our previous discussions on viruses but will be elaborated on in this chapter.

In general, virus scanners work in two ways. First, a virus scanner may contain a list of all known virus definitions—that is, files that list known viruses and their file sizes, properties, and behaviors. Generally, one of the services that vendors of virus scanners provide is to periodically update these files. A virus definition list is typically in a small file, often called a *.dat* file (short for data). When you update your virus definitions, what actually occurs is that your current file is replaced by the more recent one available from the vendor. The antivirus program can then scan your PC, network, and incoming email for known virus files. Any file on your PC or attached to an email is compared to the virus definition file to see whether there are matches. With emails, this can be done by looking for specific subject lines and content. The virus definitions often also include details on the file, file size, and more. This provides a complete signature of the virus.
