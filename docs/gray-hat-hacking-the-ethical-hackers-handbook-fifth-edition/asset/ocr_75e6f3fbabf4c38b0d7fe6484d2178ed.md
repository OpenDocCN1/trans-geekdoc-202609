![](bbox=[0.135, 0.08, 0.255, 0.16])

NOTE Remember to change the IP address to match your vulnerable server and verify that you have created the test1 user account on your Windows VM.

It turns out in this case that the vulnerability exists in a child process, wsshd.exe, that only exists when there is an active connection to the server. Therefore, we will need to launch the exploit and then quickly attach the debugger to continue our analysis. This is why the sleep() function is being used with an argument of 15 seconds, giving us time to attach. Inside the VMware machine, you may attach the debugger to the vulnerable program by choosing File | Attach. Select the wsshd.exe process and then click the Attach button to start the debugger.

![](bbox=[0.135, 0.39, 0.255, 0.46])

NOTE It may be helpful to sort the Attach screen by the Name column to quickly find the process. If you need more time to attach, you may increase the number of seconds passed as an argument to the sleep() function.

Here goes! Launch the attack script from Kali with the following command and then quickly switch to the VMware target and attach Immunity Debugger to wsshd.exe:

```
#python prosshd1.py
```

![](bbox=[0.16, 0.61, 0.84, 0.84])

Once the debugger starts and loads the process, press F9 to “continue” the program. At this point, the exploit should be delivered and the lower-right corner of the debugger