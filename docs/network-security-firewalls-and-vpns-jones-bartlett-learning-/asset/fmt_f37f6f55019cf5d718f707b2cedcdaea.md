
## Next, consider whether an open-source solution is a viable option for your corporate culture.

Some organizations are philosophically opposed to open-source solutions, while others embrace and encourage such endeavors.

Do you want to include the option to build your own or focus on only off-the-shelf, ready-to-deploy options? Making this decision early will help guide you toward a viable choice.

Familiarize yourself with the wirespeed of the network, general traffic levels, the types of filtering desired, types or forms of recent attacks, and future growth and expansion plans. Armed with these pieces of information, you can begin a serious hunt for the most appropriate firewall solutions.

The firewall technology advances quickly. Often, new attacks and exploits crafted by hackers drive these advancements and upgrades. A specific recommendation for a specific model, product line, or even vendor has a finite life. Suggestions you hear today are likely to be out of date, superseded, or compromised in a few short months. Products at the top of the market one year might not even place in the next.

Seek out current firewall reviews both online and in technical publications and trade journals. Find firewall options that fall within the parameters you laid out based on your understanding of the network and known threats.

Some general guidelines will assist you in this process:

![Image](images/bull1.jpg) If speed, flexibility, and simplicity are priorities, then select a packet filtering firewall or a stateful inspection firewall.

![Image](images/bull1.jpg) If real-time applications and high-bandwidth communications are priorities, then select a dedicated application-specific proxy firewall.

![Image](images/bull.jpg) If strong authentication is a priority, then select an application gateway firewall or a dedicated application-specific proxy firewall.

![Image](images/bull1.jpg) If detailed logging is a priority, then select an application proxy firewall.

![Image](images/bull1.jpg) If customized, unique, or complicated filtering options are a priority, then select a dedicated application-specific proxy firewall or a stateful inspection firewall.

![Image](images/bull1.jpg) If stopping internal attacks is a priority, then select a dedicated application-specific proxy firewall or a personal host firewall.

A single firewall product rarely satisfies every need. However, you should be able to find one or more firewall solutions that address the primary security concerns of your organization.

## The Difference Between Buying and Building a Firewall

Carefully consider the choice of whether to buy a ready-to-deploy firewall versus building it yourself. An off-the-shelf firewall that you simply plug in can be an attractive solution. However, an out-of-the-box product will generally cost more than an equivalent do-it-yourself system. In addition, most pre-configured systems are not as flexible or expandable as a custom-built version.

That’s not to say that a do-it-yourself firewall is always the best answer, either. A self-constructed firewall can be less expensive and provide a wider variety of features and options. However, when an in-house, custom firewall experiences a problem, you can usually find little formal technical support beyond a user-community discussion forum.

If you are prepared to fully research and understand a firewall product to install, configure, and manage it yourself, then a do-it-yourself firewall can be a great cost-saving solution. However, if your organization’s IT staff is already stretched and overworked, then home-built solutions will likely cause more problems than they solve.

A pre-built, off-the-shelf firewall is more likely to work right out the box, requiring only that you plug it in, set the configuration, and connect the network cables. A build-it-yourself firewall may require additional hardware manipulation, juggling of device drivers, hardening of a host OS, and so on. Ask yourself: Is custom-built worth the hassle?

Don’t automatically reject either buy or build firewall options before you research and assess the options. You might be surprised at the low cost and feature richness of a boxed product or caught off guard by the complexity, instability, or high-cost of a do-it-yourself product. Always look for the best firewall solution for your specific needs and current threats.

![Image](images/note.jpg)

> **NOTE**
>
> Build-it-yourself firewalls are usually less costly because they usually don’t include dedicated hardware and often use open-source (free) source code. However, the tradeoff for the savings to successfully deploy a reliable border sentry solution is that you need to know more about firewalls generally and your specific software and/or hardware.

## Mitigating Firewall Threats and Exploits

Firewalls are one of the most important components of a complete security solution. However, they are not without their own issues, threats, and concerns. Exploits will cause a firewall to fail. Remember that a firewall is software that sometimes includes dedicated hardware and a host operating system. Any software product is prone to flaws and errors in programming. Simply calling it a firewall does not eliminate this concern.

Ultimately, firewalls are software code written by human beings. In either a host firewall or an appliance firewall, the logic and controlling mechanisms of the firewall are software code. Software code is designed and written by people. And whenever people are involved, mistakes or oversights are possible.

Coding errors are not as common in firewall products as in operating systems or other forms of software. But don’t think they don’t occur. Most firewall programmers and vendors take extra care to comb through and test every line of code to exacting quality control and security standards. Standard industry practice requires considerable pilot testing of firewall code before release into the commercial environment.

In spite of these precautions, firewalls have in the past been released to market with software coding errors later discovered and exploited. Hackers are constantly using scanning, testing, and probing tools to discover exploitable weaknesses. When a vulnerability appears, hackers take advantage of the flaw. Some firewall exploits have caused firewalls to freeze or crash, while others have given the hacker the ability to read or adjust filtering rules. In most cases, vendors quickly release updates and patches to correct these problems. When selecting a firewall, check the version and patching history. Firewall products with lots of patches might not be as reliable in the future as a product with fewer patches.

How long does the vendor typically take to release a patch once a flaw or exploit for the product becomes public knowledge? The longer the vendor takes to release a fix, the longer you will be left insecure waiting for the update.

Some exploits cause buffer overflows. In a buffer overflow, a memory buffer exceeds its capacity and extends its contents into adjacent memory. Hackers often use this attack against poor programming techniques or poor software quality control. Hackers inject more data into a memory buffer than it can hold, which results in the additional data flowing over into the next area of memory. If the overflow extends to the next memory segment designated for code execution, a skilled attacker can insert arbitrary code that will execute with the same privileges as the current program. Improperly formatted overflow data may also cause a system crash.

When the firewall vendor becomes aware of an exploit in the wild, it quickly develops and releases a patch. An effective security- and patch-management system will enable you to quickly test and update the firewalls protecting your production environment. A delay in the release of a patch or its application keeps the window of opportunity for hackers to compromise your environment wide open.
