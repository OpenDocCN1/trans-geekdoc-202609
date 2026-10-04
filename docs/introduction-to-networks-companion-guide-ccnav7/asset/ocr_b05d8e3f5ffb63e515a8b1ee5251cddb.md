To move from any subconfiguration mode of the global configuration mode to the mode one step above it in the hierarchy of modes, enter the exit command.

To move from any subconfiguration mode to the privileged EXEC mode, enter the end command, as shown in Example 2-3, or enter the key combination Ctrl+Z.

# Example 2-3  Moving Directly Back to Privileged EXEC Mode

```
Switch(config-line)# end
Switch#
```

You can also move directly from one subconfiguration mode to another. In Example 2-4, notice that after an interface is selected, the command prompt changes from (config-line)# to (config-if)#.

# Example 2-4  Moving Between Subconfiguration Modes

```
Switch(config-line)# interface FastEthernet 0/1
Switch(config-if)#
```

# Video—Navigate Between IOS Modes (2.2.5)

Refer to the online course to view this video.

![](bbox=[0.12, 0.55, 0.22, 0.62])

# A Note About Syntax Checker Activities (2.2.6)

When you are learning how to modify device configurations, you might want to start in a safe, non-production environment before using real equipment. NetAcad provides a variety of simulation tools to help build your configuration and troubleshooting skills. These simulation tools typically do not have all the functionality of real equipment. One such tool is Syntax Checker. With Syntax Checker, you are given a set of instructions to enter a specific set of commands. You cannot progress in Syntax Checker unless the exact and full command is entered as specified. More advanced simulation tools, such as Packet Tracer, let you enter abbreviated commands, much as you would do on real equipment.

# Syntax Checker—Navigate Between IOS Modes (2.2.7)

Use the Syntax Checker activity to navigate between IOS command lines on a switch.

Refer to the online course to complete this activity.

![](bbox=[0.12, 0.87, 0.22, 0.93])