
## Chapter 2

35. [Figure 2.35 Using GoDaddy to place your Azure AD custom information](#c02.xhtml#figure2-35)

36. [Figure 2.36 Adding the CNAME records for smooth auto-enrollment](#c02.xhtml#figure2-36)

37. [Figure 2.37 Testing the CNAME before continuing](#c02.xhtml#figure2-37)

38. [Figure 2.38 The goal is to validate the domain first (left). Then change the default primar…](#c02.xhtml#figure2-38)

39. [Figure 2.39 The user name field will not permit you to add a domain you don’t own. You’ll s…](#c02.xhtml#figure2-39)

40. [Figure 2.40 You can see your new user with the custom domain name.](#c02.xhtml#figure2-40)

41. [Figure 2.41 Assign your new user a license.](#c02.xhtml#figure2-41)

42. [Figure 2.42 Now you can have local Windows admins enroll users using your custom domain nam…](#c02.xhtml#figure2-42)

43. [Figure 2.43 You need to add the name of your verified Azure AD domain here in on-prem AD Do…](#c02.xhtml#figure2-43)

44. [Figure 2.44 Use Express Settings to connect your (simple) on-prem AD to Azure AD.](#c02.xhtml#figure2-44)

45. [Figure 2.45 Give it the credentials you used when setting up your E5 account.](#c02.xhtml#figure2-45)

46. [Figure 2.46 Provide the on-prem AD domain administrator credentials.](#c02.xhtml#figure2-46)

47. [Figure 2.47 Be sure your UPN and Azure names match as Verified.](#c02.xhtml#figure2-47)

48. [Figure 2.48 The AD Connect sync wizard is complete.](#c02.xhtml#figure2-48)

49. [Figure 2.49 Refresh the page to see the newly synced users. Note new users are coming from …](#c02.xhtml#figure2-49)

50. [Figure 2.50 Each user needs to have the correct suffix in on-prem AD for it to be synchroni…](#c02.xhtml#figure2-50)

51. [Figure 2.51 Launching the Synchronization Service](#c02.xhtml#figure2-51)

52. [Figure 2.52 Using PowerShell to force an AD to AAD sync](#c02.xhtml#figure2-52)

53. [Figure 2.53 See that your one user has successfully come over from on-prem AD to Azure AD. …](#c02.xhtml#figure2-53)

54. [Figure 2.54 After the on-prem AD PowerShell command, then a sync to Azure AD, all accounts …](#c02.xhtml#figure2-54)

55. [Figure 2.55 How to nuke a user who is syncronized from on-prem AD](#c02.xhtml#figure2-55)

56. [Figure 2.56 Use the Register domain-joined computers as a devices’ policy to prevent Window…](#c02.xhtml#figure2-56)

57. [Figure 2.57 You need to specifically set up Azure AD to also sync Windows 10 computers.](#c02.xhtml#figure2-57)

58. [Figure 2.58 How to see Hybrid Azure AD joined machines](#c02.xhtml#figure2-58)

59. [Figure 2.59 Before a machine is automatically Azure AD joined](#c02.xhtml#figure2-59)

60. [Figure 2.60 After a machine is automatically Azure AD joined](#c02.xhtml#figure2-60)

61. [Figure 2.61 You can see computers joined to Azure AD through the `get-msoldevice` PowerShel…](#c02.xhtml#figure2-61)

## Chapter 3

1. [Figure 3.1 After you enroll a device, you get a success message.](#c03.xhtml#figure3-1)

2. [Figure 3.2 The Info button within Access Work or school. Local Admins see what’s on the le…](#c03.xhtml#figure3-2)

3. [Figure 3.3 The Sync button is like `GPUpdate` for MDM.](#c03.xhtml#figure3-3)

4. [Figure 3.4 Click a profile type to see policies’ types within that profile type.](#c03.xhtml#figure3-4)

5. [Figure 3.5 Making your first Device restriction policy to manage Microsoft Edge Browser](#c03.xhtml#figure3-5)

6. [Figure 3.6 Use the Assignments blade to assign your policy to All Devices.](#c03.xhtml#figure3-6)

7. [Figure 3.7 Your first MDM policy sets the Windows Edge home page to the value of your choi…](#c03.xhtml#figure3-7)

8. [Figure 3.8 Use the MDM Advanced Diagnostic Report to see your settings.](#c03.xhtml#figure3-8)

9. [Figure 3.9 Don’t be fooled: Not every CSP with familiar names will work as expected on Win…](#c03.xhtml#figure3-9)

10. [Figure 3.10 Some MDM policies will work for both User and Device.](#c03.xhtml#figure3-10)

11. [Figure 3.11 Getting to know a setting before deploying and testing it](#c03.xhtml#figure3-11)

12. [Figure 3.12 Using Microsoft Intune to block Cortana](#c03.xhtml#figure3-12)

13. [Figure 3.13 See MDM setting AllowCortana in the PolicyManager section of the Registry.](#c03.xhtml#figure3-13)

14. [Figure 3.14 When the MDM profile is removed AllowCortana returns to 1 (Enabled).](#c03.xhtml#figure3-14)

15. [Figure 3.15 The preview of Administrative Templates node in Intune](#c03.xhtml#figure3-15)

16. [Figure 3.16 The list of curated ADMX settings in a flat list in Intune](#c03.xhtml#figure3-16)

17. [Figure 3.17 Searching for relevant ADMX settings](#c03.xhtml#figure3-17)

18. [Figure 3.18 An example ADMX-backed setting](#c03.xhtml#figure3-18)

19. [Figure 3.19 Adobe Flash enabled by default within IE](#c03.xhtml#figure3-19)

20. [Figure 3.20 The Group Policy setting we’re going set, but using MDM](#c03.xhtml#figure3-20)

21. [Figure 3.21 Create a Custom profile type for ADMX-backed policies with no GUI.](#c03.xhtml#figure3-21)

22. [Figure 3.22 Creating a custom OMA-URI setting](#c03.xhtml#figure3-22)

23. [Figure 3.23 Flash should stop functioning in IE now.](#c03.xhtml#figure3-23)

24. [Figure 3.24 No Group Policy involved, yet the Policies keys are manipulated.](#c03.xhtml#figure3-24)

25. [Figure 3.25 Foxit Reader’s default update behavior](#c03.xhtml#figure3-25)

26. [Figure 3.26 How you would use Group Policy to set Foxit Reader to stop automatic updates](#c03.xhtml#figure3-26)

27. [Figure 3.27 Create a profile for Foxit policies with the Custom type.](#c03.xhtml#figure3-27)

28. [Figure 3.28 Adding an ADMX file as a custom OMA-URI. The whole ADMX file gets downloaded to…](#c03.xhtml#figure3-28)

29. [Figure 3.29 Find the policy setting within the ADMX you want to deliver.](#c03.xhtml#figure3-29)

30. [Figure 3.30 Add the value to disable Foxit Updater. You can deliver the value to Device (le…](#c03.xhtml#figure3-30)

31. [Figure 3.31 You can see the ingested custom ADMX policies in the MDM sync (after you close …](#c03.xhtml#figure3-31)

32. [Figure 3.32 Successful lockout of Foxit reader with ingested ADMX file](#c03.xhtml#figure3-32)

33. [Figure 3.33 The entire ADMX downloaded into the Registry](#c03.xhtml#figure3-33)

34. [Figure 3.34 The Group Policy location is written to by the ADMX.](#c03.xhtml#figure3-34)

35. [Figure 3.35 How to start to create groups in Intune](#c03.xhtml#figure3-35)

36. [Figure 3.36 Creating Assigned groups (containing users)](#c03.xhtml#figure3-36)

37. [Figure 3.37 Creating a Dynamic computer or user group](#c03.xhtml#figure3-37)

38. [Figure 3.38 See the number of devices or users in a Dynamic group and/or click Members to s…](#c03.xhtml#figure3-38)

39. [Figure 3.39 Advanced rules utilize a query language, and you can learn more about the query…](#c03.xhtml#figure3-39)

40. [Figure 3.40 Use this query to find only Windows 1809 machines.](#c03.xhtml#figure3-40)

41. [Figure 3.41 The full list of fields you can use for Dynamic groups](#c03.xhtml#figure3-41)

42. [Figure 3.42 You can see the “Membership last updated” value for your Dynamic group.](#c03.xhtml#figure3-42)

43. [Figure 3.43 You can select groups which will accept settings.](#c03.xhtml#figure3-43)

## Chapter 4

1. [Figure 4.1 The old Microsoft Intune and SCCM hybrid design with the Intune Connector](#c04.xhtml#figure4-1)

2. [Figure 4.2 Simplified version of on-prem and cloud co-management](#c04.xhtml#figure4-2)

3. [Figure 4.3 Microsoft SCCM co-management screen to decide which technology will handle what…](#c04.xhtml#figure4-3)

4. [Figure 4.4 Co-management with all of its moving parts](#c04.xhtml#figure4-4)
