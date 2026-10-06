# FIGURE 19-4
Completed role service installation via PowerShell

![](bbox=[0.343, 0.098, 0.715, 0.169])

# REGISTERING NATIVE MODULES USING IIS MANAGER

When it comes to native modules, you could register a native module using the IIS Manager GUI. This is not as intuitive as using Server Manager but if you are the kind of administrator who prefers to spend your day using one utility and IIS Manager is your preference, you can accomplish this very important task in IIS Manager. To register a native module on the fly, follow these steps:

+   1. Launch IIS Manager, and connect to or highlight a specific IIS server that you want to examine using the Connections pane on the left.
2. The center page of IIS Manager reflects the categories of management tools by default.
3. Within the IIS category, click the Modules icon to see a list of modules installed on the server level.
4. Click the Configure Native Modules hyperlink from the modules-specific Actions pane on the right.
This produces a dialog box listing the native modules currently installed (see Figure 19.5).
5. Click the Register button in the dialog box to manually register a native module on the fly. This, of course, requires that you know the actual filename of the native module.
6. Upon adding the native module to the list, select it to enable it at the server level.

# FIGURE 19.5
Configure Native Modules dialog box

![](bbox=[0.343, 0.64, 0.725, 0.888])