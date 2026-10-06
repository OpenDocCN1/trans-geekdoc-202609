# WELCOME BACK START BUTTON

In Windows Server 2012 to get to your program listing's shown in the following graphic, you had to hit the Windows key on your keyboard to the left of the left Alt key. In Windows Server 2012 R2 the Start Button has returned to its original position in the lower left corner of the task bar. This will once again allow you quick access to your main programs drop-down menu that get installed with Windows Server 2012. As you add programs and roles, you will see the new buttons added here.

![](bbox=[0.238, 0.259, 0.843, 0.613])

# SERVER MANAGER TIP!

Server Manager has a habit of popping up every time you log in. That will get pretty old in a very short time. You can control this by editing the REG_DWORD value of DoNotOpenServerManagerAtLogon in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Server Manager. The default is 0, which causes Server Manager to appear every time you log. Setting it to 1 will disable this. Another way to disable Server Manager from appearing at login is to select the Server Manager drop-down menu in the top-right corner of Server Manager. Then select Server Manager Properties. A small pop-up will appear with check box called "Do not show me this console at logon." You will probably want to select this because waiting for Server Manager to open and closing it every time you log in could rapidly become tiresome.