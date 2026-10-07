
# Understanding Google Cloud Identity

In this chapter, we will look at Google Cloud Identity, which is Google's Identity as a Service (IDaaS) and Enterprise Mobility Management (EMM) product. We will cover aspects such as directory management, how to create and manage user accounts and groups, and how to sync directory services such as Google Cloud Directory Sync (GCDS). There are other features and services that will be covered, including Single Sign-On (SSO) and device and application management.

Furthermore, we will look at how you can use Google Cloud Identity to enforce 2-step verification (2SV), password management, session management, and reporting and admin log activity. The topics within Cloud Identity are very broad and cover some aspects that are related to Google Workspace (formerly Known as G Suite) we will limit our discussion in this chapter to the topics that are relevant to the Google Professional Cloud Security Engineer exam.

In this chapter, we will cover the following topics:

- Overview of Cloud Identity
- Account security, such as configuring users, two-factor authentication, session management, and SAML
- How to configure Google Cloud Directory Sync

# Overview of Cloud Identity

Google Cloud Identity is different from some of the other cloud security products that we will cover in this book. What makes it different is that it covers two different platforms: Google Workspace and Google Cloud. Google Workspace is out of scope as it's not covered in the Google Professional Cloud Security Engineer exam; the features and aspects that we will cover will only pertain to the use of Cloud Identity with regard to Google Cloud.

First, let's understand a few aspects of Cloud Identity. Cloud Identity is accessed via a separate console (admin.google.com). Cloud Identity is also the first product that you will interact with when you configure your Google Cloud environment, as the super administrator account exists in Cloud Identity. There will be more on the super administrator account later in this chapter. Cloud Identity only provides an authentication service and not authorization. The authorization aspect is covered by Google Cloud Identity and Access Management (IAM), which is accessed via the Google Cloud console (console.google.com).

Before we get into the configuration and setup of Cloud Identity, let's look at some of the key features to better understand Cloud Identity. Cloud Identity is the same IDaaS that powers Google Workspace, and it's available both as a free version and a premium version. The premium version has no cap on the number of users, although you can ask Google in the free version to increase the number of users from the default 50-user limit. The other differences include the premium version's support for Secure LDAP, access to the Google security center, mobile device management, auto-exporting audit logs to BigQuery, and session length management, which you control the duration of the authentication tokens. Finally, the free version comes with no service-level agreements (SLA's).

Now that we know about the differences between free and premium Cloud Identity, let's take a quick look at some of the features of Cloud Identity that we will cover in this chapter.

# Single pane of glass

![](img/f681dfc12450e3a4c257352b70dbceca_88_0.png)

Figure 5.1 - Google Cloud Identity features

The preceding figure captures the key features of Google Cloud Identity. Let's look at some of the features that are more relevant to Google Cloud. In terms of lifecycle management, you can create or import user accounts into a cloud-directory. If you use Active Directory in your on-premises environment, you can use the GCDS tool to configure Active Directory and import users, groups, and memberships to Google Cloud Identity.

You can control the process of provisioning and de-provisioning as users join the organization, change roles, or leave. Account security lets you enforce the use of 2SV, apply password policies, and turn on/off access to the Google Cloud console. You can also use Google Authentication or SSO with an external Identity Provider (IdP), such as Okta or Ping Identity. We will look at SSO in more detail later in this chapter.

In the next section, we will cover how to get started with Cloud Identity, beginning with setting up your domain verification. Domain verification is not covered in the exam and is included here for context.

# Identity domain setup

Before we begin, remember that Cloud Identity is accessed via admin.google.com; for the purpose of segregation the admin role, it is recommended to set up a different domain for Google Cloud if you already have a Workspace domain. Separating the Google Cloud account from the Workspace account is a good idea for governance and compliance requirements.

Configuring a new domain includes the following steps:

1. Sign up for Cloud Identity. Provide your personal details, such as your name, email address, business, geographical region, and domain name.
2. The next step is to perform a domain verification, to ensure that you are the owner of the domain that you are trying to set up.

If you know your domain registrar is, you can select the name and then follow the guidance from the Cloud Identity web interface to verify the domain. If registrar-specific guidance provided, which can be accessed from this link: https://packt.link/QiqIk.

If you do not have your registrar listed and get generic guidance on how to verify your domain using the method of adding a TXT record with a verification code generated from Google Workspace, you can follow the instructions provided here: https://packt.link/H2anX.

As mentioned earlier, these steps are listed for completeness so that you are the owner of the Cloud Identity domain setup. Next, we will look at the super admin user role, to secure access, and some best practices before we move on to understanding how users and groups can be created and managed.

# Super administrator best practices

Cloud Identity has super admin role, which is not the same as the Google IAM Organization Administrator, but the super admin is by default an Organization Administrator and has administrator privileges for both platforms. The super admin is managed via admin.google.com and has the access rights to manage users, groups, and security settings for Cloud Identity. It is also used to delegate access to the Cloud IAM Organization Administrator role. For all purposes, your super admin should create a Cloud IAM Organization Administrator role, but it should never be used to access console.google.com to provision or manage Google Cloud resources.

Given the importance of a super admin, there are some best practices that should be followed. These best practices include the following:

- Always enable 2SV/multi-factor authentication for the super admin account.
- Keep a backup security key in a secure location.
- Disable device trust and limit the web session length.
- Ensure resilience and over-reliance on a single individual, it is recommended to limit the usage of super admin accounts and keep the number of such accounts to a maximum of 4. This precautionary measure mitigates the risk associated with a single point of failure and ensures an adequate number of backup super admins in case of emergencies.
- Set recovery phone and email options, and ensure the recovery is secure and protected with 2SV.

> Note
> Domain DNS access to verify domain ownership is needed in the event that you lose access to super admin accounts if a recovery email/phone was not set up.

- Create a dedicated super admin account and lock it. This is a break-glass account to be used only in emergencies.
- Assign Cloud Identity roles for the delegated administration of users, groups, and so on.
- Delegate the setup and management of Google Cloud organization resources to other administrators and assign functional IAM roles to them to ensure the separation of duties.
- The Cloud Identity super admin will always bypass any SSO; they will always authenticate with Google Identity directly.

The topic of Cloud Identity is very broad and some areas overlap with Google Cloud Workspace features and functions. In this section, we only covered what is relevant from a Google Cloud Professional Security Engineer exam perspective. You can refer to the documentation for Cloud Identity if you wish to learn further. Next, we will cover some account-security-related features of Cloud Identity.
