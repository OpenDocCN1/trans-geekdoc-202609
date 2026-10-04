# Advanced cloud defense

Now that you know how to address recommendations in order to enhance the security posture of your cloud workloads, you need to ensure that you also apply security controls to reduce the attack surface. In this chapter, you will learn how Azure Security Center can help you harden your resources. You will learn how to use just-in-time virtual machine (VM) access to harden the access to Azure VMs and to ensure that your VMs are not always exposed to the Internet. You will learn how to track changes to your files and registry file integrity monitoring, and you will also learn how Security Center uses machine learning to create application whitelisting.

# Just-in-time virtual machine access

To provide remote access to VMs, the public cloud infrastructure provider must allow all remote management traffic to those VMs. To do this, you use RDP, SSH, and remote Power-Shell. Using these tools is easy—and nothing beats easy. Unfortunately, easy is often the enemy of security, so it's a difficult balancing act.

> NOTE There are alternative methods for providing remote management access to VMs. Such methods include point-to-site VPN, site-to-site VPN, and vari-eties of dedicated WAN link solutions.

The most common attack against VMs in Azure (and other public cloud service providers) is an RDP or SSH brute-force attack. VMs are continuously hit by attempts to log on. If you have a strong password policy, it's unlikely your VMs will be compromised. However, if you're a security professional, you already know that most password policies are not strong and that users often use easy-to-guess passwords.

You can take various steps to reduce the chance of compromise because of a brute-force attack, but you probably don't want to hand over these tasks to your public cloud service provider. However, you might want to consider letting your public cloud service provider help you with network access to management ports to your VMs. That's Azure Security Center just-in-time (JIT) VM access. It allows you to control who can gain access to predefined management ports on a VM, when, and for how long.