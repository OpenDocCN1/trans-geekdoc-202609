# CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

For a detailed procedure on raising domain and forest functional levels, see the section, “Raising Domain and Forest Functional Levels.”

# Introduction to Windows Azure Active Directory

We previously discussed Active Directory is on-premises. This means that Active Directory within your company is protected from the outside world. Let’s recall why you use Active Directory. You need this service to centrally store and manage all your users and computers to control the behavior of your Windows infrastructure.

A few years after Active Directory was developed, IT had a big problem. Without Active Directory, every application needed to store its access credentials in a store, such as in a database or on the server itself. Windows NT had a modest way of managing users and computers, but that solution was far from meeting the needs of an enterprise. One reason why Active Directory was developed to centrally manage the infrastructure. The same problem occurred in Windows Azure. Now the application landscape has fragmented with some of usernames and passwords that the application can authenticate and authorize the user to use this application in Azure. But now Windows Azure Active Directory comes into play. In this section we refer to your on-premises Active Directory as “Active Directory” and Azure-hosted Active Directory as “Windows Azure Active Directory” (WAAD, Windows Azure AD, or Azure Directory).

Windows Azure Directory is a service that provides identity and access-control capabilities for your cloud applications. Many online applications use Windows Azure AD. The most of these is Office 365; others use Dynamics CRM Online and Windows Directory.

WAAD is a multtenant service that can handle millions of companies, for more than 100 million users, and thousands of tenants on the same platform. It is optimized for availability and consistent performance for scalability. That means you can no longer need your on-premises Active Directory? Yes and no. Windows Azure AD can be used on its own, but the most common scenario is that in architecture, it can be considered as Active Directory in the cloud extended from your on-premises Active Directory (See Figure 7.69).

Providing this expansion from your on-premise Active Directory into the cloud allows you to manage your users and groups locally and replicate them to WAAD using DirSync, which we will discuss shortly. Because of mechanism, you will be able to create a single sign-on (SSO) experience for your cloud-hosted application. After that if you are using only DirSync you won't get an SSO experience. For SSO you also need to deploy Active Directory Federation Services (AD FS) in your on-premises Active Directory. For more details, see the section, “Active Directory Logon Favors.”

# Getting Started with Windows Azure Active Directory

How do you get an account for an AD tenant in Azure Active Directory? The easiest way is to sign up for an Office 365 account, and you will immediately have Windows Azure Active Directory along with it. This is because Office 365 uses Windows Azure Active Directory. Another way of getting WAAD is to sign up for it online on Windows Azure (http://www.windowsazure.com/). Which method you choose, you will be able to manage your account from both portals.

After you have signed up for Windows Azure, you can start managing your directory, as shown in Figure 7.70.