A second, more subtle point is that of the virtual network configuration. How does the VM know which virtual switches to use on the new host? Internally, each virtual switch is known by its GUID, allowing you to give any name you like without interfering with its relations to virtual NICs. But if you create a virtual switch on another host, it will have a different GUID. Hyper-V has one little trick to get around this. On import, it looks for virtual switches with exactly the same name (including character case) as the ones included in the export files. If it finds them, the virtual NICs are connected. If not, the imported VM will disconnected switches.

Let's walk through an example where you export and import a VM. Any VM will do, but in this case we will use W50212R2-SRV1. Ideally you would have a second Hyper-V host for, but the export works with one.

Assume you have a shared folder; we'll use VMHOST with a descriptive name like ImportedVMs. The required share permissions for this folder are a bit tricky. The export process runs as SYSTEM, not as you. So, the share should have permissions for the host computer to write data. Use either the computer account of the source host (VMHOST1-SRV in our example) or the Everyone security to write access. Then, start the export process on the source host:

+   1. On the Hyper-V management console, select the VM to export, which is WS5021R2-SRV1 in this.

+   2. With the VM still running, choose the Export option from the Actions pane.

+   3. Enter a destination path for your export.

This can be a local drive, USB drive, or a remote location. This time, we will export directly to another Hyper-V host: \vmhost2-srv\ImportedVMs. If the path does not exist, the wizard will create it. Whatever path you specify here, the wizard will create a subdirectory with the VM.

After the export procedure is finished, you import the VM. You can do this from the Hyper-V management console on the server side by adding the target host as an additional machine, but for example you will log on to the target:

+   1. Log on to VMHOST2-SRV with an administrative account and open the Hyper-V management console.

+   2. If you want the virtual NICs to connect automatically on import, make sure there are virtual switches on both hosts with exactly the same names.

In our example, we use MGMTNIC for management and VMEXT1 for external connectivity.

+   3. From the Actions pane in the Hyper-V management console, select Import Virtual Machine; then click Next.

+   4. In the Locate Folder dialog box, input or browse for the path where the exported VM is stored as D:\ImportedVMs\W50212R2-SRV1 and then click Next.

+   5. In the Select Virtual Machine dialog box, ensure you select the correct version of the VM to import; then click Next to move on.