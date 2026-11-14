CAUTION Before you consider paying the ransom, it's suggested that you consult the nearest technical support person to try to regain control of your data.

Now that you have an overview of how ransomware works, let's dissect a couple of examples to understand their inner workings.

# Dissecting Ransomlock

When you're dealing with ransomware, dynamic analysis is useless most of the time. This is because once you run it, your Desktop will be controlled by the malware; therefore, you will not be able to review the logs or results from the monitoring tool. However, there are many tricks you can perform in order to recover the machine after running the malware to get access to the monitoring results. In this section, we take a look at a Ransomlock malware sample that belongs to the Locker ransomware family and implements the techniques typical for this class of ransomware.

![](bbox=[0.135, 0.405, 0.26, 0.475])

NOTE The exercises in this chapter are provided as examples rather than as labs due to the fact that in order to perform these exercises, you need a malicious binary.

# Example 19-1: Dynamic Analysis

![](bbox=[0.135, 0.605, 0.26, 0.68])

NOTE The MD5 hash of the Ransomlock sample that will be analyzed in this section is ED3AEF329EBF4F6B11E1C7BABD9859E3.

Ransomlock will lock the screen but will not try to kill any processes or deny network access to the machine. Therefore, as analysts, we can leave a backdoor in the virtual machine (VM) to kill the malicious process at any time and recover control of the infected system. Let's see how this works:

+   1. We need to create a bind shell to get remote access to the infected machine. We can use Metasploit in our Kali machine to do that, as shown here, making sure to change the RHOST to your IP. Because no port is defined, the default one will be 4444.