# **Mechanics of Patching**

+   - Microsoft Windows Server looks for updates (patches) automatically
+   - It also can install updates automatically
+   - Linux distributions often use rpm

# **Problems with Patching**

+   - Companies get overwhelmed by number of patches
+     - Use many programs; vendors release many patches per product
+     - Especially a problem for a firm’s many application programs
+   - Cost of patch installation
+     - Each patch takes some time and adds to labor costs
+     - Mitigated by patch management servers that find vulnerabilities and patches and then distribute patches to general servers
+   - Prioritization
+     - Often lack the resources to apply all; must be selective
+     - Prioritize patches by criticality
+     - May not apply all patches, if risk analysis does not justify them
+   - Patch management servers reduce costs
+     - Download patches from software vendors
+     - Find vulnerable computers in the firm automatically and push patches out to them
+   - Risks of patch installation
+     - Reduced functionality
+     - Freeze machines, do other damage—sometimes with no uninstall possible
+     - Should test on a test system before deployment on servers

**Figure 7-13** Applying Patching (Study Figure)

**Figure 7-14** Windows Server Update Services

![](bbox=[0.301, 0.642, 0.889, 0.993])