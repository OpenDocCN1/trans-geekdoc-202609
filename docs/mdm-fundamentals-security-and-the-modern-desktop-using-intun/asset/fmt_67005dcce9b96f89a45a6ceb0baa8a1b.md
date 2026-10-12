
## Chapter 8

23. [Figure 8.23 See which devices will get the Autopilot profile you created.](#c08.xhtml#figure8-23)

24. [Figure 8.24 The default “All users and all devices” settings, which I recommend you use in …](#c08.xhtml#figure8-24)

25. [Figure 8.25 Additional enrollment options (which I don’t recommend for the chapter, but use…](#c08.xhtml#figure8-25)

26. [Figure 8.26 Configuring Azure AD branding, which you’ll see in Autopilot](#c08.xhtml#figure8-26)

27. [Figure 8.27 Using Sysprep to get back to the OOBE](#c08.xhtml#figure8-27)

28. [Figure 8.28 Click “Get started” to reset this PC and provide admin credentials; then follow…](#c08.xhtml#figure8-28)

29. [Figure 8.29 You can see Autopilot is working when you see your company’s custom welcome.](#c08.xhtml#figure8-29)

30. [Figure 8.30 Waiting for Autopilot to finish configuring the machine](#c08.xhtml#figure8-30)

31. [Figure 8.31 Autopilot details expanded](#c08.xhtml#figure8-31)

32. [Figure 8.32 Seeing your existing dynamic group](#c08.xhtml#figure8-32)

33. [Figure 8.33 Assigning Autopilot to the “Computers with ‘Computer’ in the Name” group](#c08.xhtml#figure8-33)

34. [Figure 8.34 Converting targeting devices for Autopilot.](#c08.xhtml#figure8-34)

35. [Figure 8.35 Seeing newly imported devices in Autopilot](#c08.xhtml#figure8-35)

36. [Figure 8.36 Use Windows+Ctrl+R at the login screen to start a reset there.](#c08.xhtml#figure8-36)

37. [Figure 8.37 The different kinds of wipes and resets in Intune](#c08.xhtml#figure8-37)

38. [Figure 8.38 How to marry a user to a specific hardware ID](#c08.xhtml#figure8-38)

39. [Figure 8.39 The result when a machine starts up with Autopilot and a user is married to a h…](#c08.xhtml#figure8-39)

40. [Figure 8.40 Autopilot self-deploying mode requires a TPM 2.0 chip which is capable of attes…](#c08.xhtml#figure8-40)

41. [Figure 8.41 The OrderID is seen in the Deployment Group field in Autopilot.](#c08.xhtml#figure8-41)

42. [Figure 8.42 Creating a dynamic group to capture a specific OrderID (ORDER1 in this case)](#c08.xhtml#figure8-42)

43. [Figure 8.43 Select Self-Deploying as the deployment mode within the profile.](#c08.xhtml#figure8-43)

44. [Figure 8.44 Pre-answering the OOBE questions for self-deploying devices](#c08.xhtml#figure8-44)

45. [Figure 8.45 Specifying the dynamic group to which the Autopilot profile will apply](#c08.xhtml#figure8-45)

46. [Figure 8.46 Specifically excluding the self-deploy devices from the user-driven devices](#c08.xhtml#figure8-46)

47. [Figure 8.47 Autopilot asks no questions to self-deploy machines when Ethernet is used.](#c08.xhtml#figure8-47)

48. [Figure 8.48 Flow diagram of Hybrid Azure AD Join](#c08.xhtml#figure8-48)

49. [Figure 8.49 Creating and inspecting an Offline Domain Join (ODJ) blob](#c08.xhtml#figure8-49)

50. [Figure 8.50 Performing a by-hand domain-join with an ODJ blob](#c08.xhtml#figure8-50)

51. [Figure 8.51 Delegate Control over your known default location. If it’s not the Computers fo…](#c08.xhtml#figure8-51)

52. [Figure 8.52 Enable Computers as an Object Type.](#c08.xhtml#figure8-52)

53. [Figure 8.53 Specify the computer where you plan to install the Intune Connector for Active …](#c08.xhtml#figure8-53)

54. [Figure 8.54 Specify that the computer can perform the selected delegated items.](#c08.xhtml#figure8-54)

55. [Figure 8.55 Select Full Control on the Permission page.](#c08.xhtml#figure8-55)

56. [Figure 8.56 Downloading the Intune Connector for Active Directory](#c08.xhtml#figure8-56)

57. [Figure 8.57 Installing the Intune Connector for Active Directory](#c08.xhtml#figure8-57)

58. [Figure 8.58 After you give the Global Admin’s credentials, you will get a success message f…](#c08.xhtml#figure8-58)

59. [Figure 8.59 Inspecting the Intune ODJConnector Service](#c08.xhtml#figure8-59)

60. [Figure 8.60 Finding the ODJ Service event log](#c08.xhtml#figure8-60)

61. [Figure 8.61 An event log item from the ODJ Connector Service](#c08.xhtml#figure8-61)

62. [Figure 8.62 The Intune Connector should show you the connection, if it’s active, and last s…](#c08.xhtml#figure8-62)

63. [Figure 8.63 You can select User-Driven and “Hybrid Azure AD joined” to enroll in both MDM a…](#c08.xhtml#figure8-63)

64. [Figure 8.64 Create a Domain Join profile to tell the machine how to connect to your Active …](#c08.xhtml#figure8-64)

65. [Figure 8.65 The Domain Join settings for the device configuration profile](#c08.xhtml#figure8-65)

66. [Figure 8.66 You can see that you’ve joined Active Directory here.](#c08.xhtml#figure8-66)

67. [Figure 8.67 With Hybrid joined Windows 10 machines, you must log on with an on-prem Active …](#c08.xhtml#figure8-67)

68. [Figure 8.68 Computers appear in the Computers folder after they join Active Directory.](#c08.xhtml#figure8-68)

69. [Figure 8.69 The 80070774 message means the computer cannot complete the ODJ handshake with …](#c08.xhtml#figure8-69)

70. [Figure 8.70 Error message when the computer is already MDM enrolled](#c08.xhtml#figure8-70)

71. [Figure 8.71 Autopilot provisioning after OOBE starts and the Windows key is pressed five ti…](#c08.xhtml#figure8-71)

## Chapter 9

1. [Figure 9.1 How both traditional and modern devices use the same Windows Update Service.](#c09.xhtml#figure9-1)

2. [Figure 9.2 Setting up WUfB policies in Intune](#c09.xhtml#figure9-2)

3. [Figure 9.3 Assigning a Windows 10 update ring to a group of computers](#c09.xhtml#figure9-3)

4. [Figure 9.4 The Office Update Channel Group Policy setting](#c09.xhtml#figure9-4)

5. [Figure 9.5 The Intune Administrative Template setting](#c09.xhtml#figure9-5)

6. [Figure 9.6 Running the Office Readiness Toolkit](#c09.xhtml#figure9-6)

7. [Figure 9.7 Choosing your report location and some other options](#c09.xhtml#figure9-7)

8. [Figure 9.8 Advanced reports send data to Microsoft to evaluate your machine’s data.](#c09.xhtml#figure9-8)

9. [Figure 9.9 The Readiness Toolkit starts to create the report.](#c09.xhtml#figure9-9)

10. [Figure 9.10 Click Enable Content to display your report.](#c09.xhtml#figure9-10)

11. [Figure 9.11 The add-in readiness report](#c09.xhtml#figure9-11)

12. [Figure 9.12 Using App Health Analyzer on one machine in interactive mode](#c09.xhtml#figure9-12)

13. [Figure 9.13 The “Device compliance” section is on the left, but Intune’s default Status val…](#c09.xhtml#figure9-13)

14. [Figure 9.14 Creating a device compliance policy](#c09.xhtml#figure9-14)

15. [Figure 9.15 Setting Require BitLocker to Require as a compliance setting](#c09.xhtml#figure9-15)

16. [Figure 9.16 Creating a device compliance policy to check for the Windows Firewall to be on….](#c09.xhtml#figure9-16)

17. [Figure 9.17 Seeing your two policies (and having only one enabled).](#c09.xhtml#figure9-17)

18. [Figure 9.18 Selecting one or many actions for noncompliance](#c09.xhtml#figure9-18)

19. [Figure 9.19 Example email that a user gets if you select to deliver an email template](#c09.xhtml#figure9-19)

20. [Figure 9.20 The end user’s view of the problem while using the Company Portal app](#c09.xhtml#figure9-20)

21. [Figure 9.21 A tale of two computers: COMPUTER2867 and COMPUTER10](#c09.xhtml#figure9-21)

22. [Figure 9.22 Checking device compliance status](#c09.xhtml#figure9-22)

## Chapter 10

1. [Figure 10.1 Finding “Security baselines” in the Microsoft Intune navigation menu](#c10.xhtml#figure10-1)

2. [Figure 10.2 New MDM Security baselines are born with each new Windows 10.](#c10.xhtml#figure10-2)

3. [Figure 10.3 Creating your baseline and giving it a name and optional description](#c10.xhtml#figure10-3)
