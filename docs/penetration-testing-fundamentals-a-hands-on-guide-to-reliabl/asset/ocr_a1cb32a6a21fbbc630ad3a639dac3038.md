Now let’s use the touch command, as shown in Figure 10-5.

![](bbox=[0.118, 0.158, 0.56, 0.226])

FIGURE 10-5 The touch Command.

Now let’s check those properties again, and in Figure 10-6 you can see them.

![](bbox=[0.118, 0.328, 0.593, 0.66])

FIGURE 10-6 File Properties After the touch Command.

It should be obvious that an attacker can use touch to cover his or her tracks rather effectively.

# nice

The nice command is very useful. It sets the priority of a given process. With priorities, the lower the number, the higher the priority. The minimum priority is 20 and the maximum priority is –20 and only a root user can assign negative priorities. However, any user can always lower the priorities of their own processes. This is shown in Figure 10-7.