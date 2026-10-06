
# Chapter 15 • Dynamic Access Control: File Shares, Reimagined....... 759

+ A New Way to Secure File Shares ..................................................................................... 760
Access Control Using Groups and User AD Attributes ............................................................ 765
Securing Data by Machine Attributes ................................................................................. . . . . 766
Centrally Control Permissions Using Templates ................................................................ 767
Using Effective Permissions to Troubleshoot Access Control ................................................ 769
Automatic File Classification ................................................................................................... 769
DAC Players: User, Device, Resources, and Claims ................................................................. 769
- User ................................................................................................................................................... 770
- Device ................................................................................................................................................ 770
- Resources ........................................................................................................................................ 770
- Claims .......................................................................................................................................................... 771
Enabling DAC ................................................................................................................................. 771
Pieces of an Access Policy ....................................................................................................... 774
Side Task ......................................................................................................................................... 778
Access Denied Assistance ............................................................................................................... 796
Claims—Using Different Attributes ............................................................................................ 799
- Step 1: Create the Claim ............................................................................................................ 800
- Step 2: Create the Resource Property ................................................................................... 802
- Step 3: Add to the Resource Property List ................................................................................ 802
- Step 4: Create Central Access Rules ................................................................................... 802
- Step 5: Create a Central Access Policy and Deploy It via Group Policy ................................ 803
- Step 6: Apply the Policy to the Engineering Folder ................................................................ 803
- Step 7: Test with Effective Access ...................................................................................... 803
Classification ........................................................................................................................... 804
Classifying a Document ........................................................................................................ 804
Classification Properties ...................................................................................................... 806
Classification Rules ................................................................................................................... 807
Expression Types ................................................................................................................................ 813
Understanding Regular Expressions ........................................................................................ 818
Securing Data Using DAC and File Classification ................................................................... 819
The Bottom Line ................................................................................................................................... 824

# Chapter 16 • Sharing Printers on Windows Server 2012 R2 Networks ......... 827

+ Print Services Overview ....................................................................................................... 827
The Printer Spooler .......................................................................................................................................... 828
The Printer Driver .............................................................................................................................. 829
Installing the Printer and Document Services Role ............................................................ 832
Adding the Printer and Document Services Role ................................................................ 832
Working in the Print Management Console ................................................................ 834
Adding the Print Services Role to Server Core ............................................................ 845
PowerShell Cmdlets Reference ................................................................................................ 847
Deploying Printers to the Masses ................................................................................ 847
Adding a Printer to a Client Manually ................................................................................ 848
Adding a Printer Using Active Directory Search ........................................................ 849
Deploying Printers via GPO ................................................................................ 853

# CONTENTS XXI

+ Viewing Deployed Printers . . . . . . . . . . . . . . . . . . . . . 856
Adjusting Print Server Settings . . . . . . . . . . . . . . . . . . . . . 857
- Server Properties . . . . . . . . . . . . . . . . . . . . . . . . . 857
- Printer Migration . . . . . . . . . . . . . . . . . . . . . . . . . 861
- Managing Printer Properties . . . . . . . . . . . . . . . . . . . . . . 862
- Printer Properties Sharing Tab . . . . . . . . . . . . . . . . . . 862
- Printer Properties Ports Tab . . . . . . . . . . . . . . . . . . 863
- Printer Properties Security Tab . . . . . . . . . . . . . . . . . . 864
- Printer Properties Advanced Tab. . . . . . . . . . . . . . . . . . 870
Managing Print Jobs . . . . . . . . . . . . . . . . . . . . . . . 876
Using Custom Filters . . . . . . . . . . . . . . . . . . . . . 878
Troubleshooting Printer Problems . . . . . . . . . . . . . . . . . . . . . . . . 879
- Basic Troubleshooting: Identifying the Situation . . . . . . 879
- Restarting the Spooler Service . . . . . . . . . . . . . . . 881
- Isolating Printer Drivers . . . . . . . . . . . . . . . . . . . . . . . . 881
The Bottom Line . . . . . . . . . . . . . . . . . . . . . . . . 882

# Chapter 17 • Remote Server Administration . . . . . . . . . . 883

+ Remote Desktop for Administration. . . . . . . . . . . 883
Configuring the Server for Remote Desktop . . . . . . . 82 884
Using Remote Desktop Connection. . . . . . . . . . . . . . 886
Remote Desktop Gateway . . . . . . . . . . . . . . . . . . . 906
Configuring a Server for Remote Assistance . . . . . . . 82 917
Windows Remote Management Service. . . . . . . . . . . 919
Enabling WinRM . . . . . . . . . . . . . . . . . . . 920
Using WinRS . . . . . . . . . . . . . . . . . . . . . 921
Remote Server Administration Tools . . . . . . . . . . 922
RSAT Compatibility Issues . . . . . . . . . . 923
- RSAT Tools. . . . . . . . . . . . . . . . . . . . . . 923
- Installing RSAT. . . . . . . . . . . . . . . . . . . . . 924
Remote Desktop and PowerShell . . . . . . . . . . 925
The Bottom Line . . . . . . . . . . . . . . . . . . . . . . 926

# Chapter 18 • Connecting Windows and Mac Clients . . . 929

+ What to Know Before You Begin . . . . . . . . . . . . . 929
Understanding Client-side Software Requirements. . . 930
Domain Accounts and Local Accounts. . . . . . . . . . . 931
Verifying Your Network Configuration . . . . . . . . . 932
Verifying Local Area Connection Settings. . . . . . . . 933
Testing Network Connectivity with the ping Command 935
Verifying and Setting Local Area Connection . . . . . . 935
Information Using the GUI. . . . . . . . . . . . . . . 935
Joining the Domain . . . . . . . . . . . . . . . . . . 942
Joining a Domain from Windows 8. . . . . . . . . . 943
Joining a Domain with PowerShell . . . . . . . . . . 950
