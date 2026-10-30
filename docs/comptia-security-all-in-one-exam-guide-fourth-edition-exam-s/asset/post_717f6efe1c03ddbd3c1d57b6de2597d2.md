
On the Internet in an attempt to sell your car, if geo-tagging was enabled on the smartphone, the location of where the photo was taken is embedded as metadata in the digital photo. Such a posting could inadvertently expose where your home is located. There has been much public discussion on this topic, and geo-tagging can be disabled on most mobile devices. It is recommended that it be disabled unless you have a specific reason for having the location information embedded in the photo.

## Application Whitelisting

As discussed in the “Application Control” section earlier in the chapter, controlling what applications a device can access may be an important element of your company’s mobile device policy. Application whitelisting and blacklisting enables you to control and block applications available on the mobile device. This is usually administered through some type of MDM capability. Application whitelisting can improve security by preventing unapproved applications from being installed and run on the device.

## Encryption

Just as the device should be encrypted, thereby protecting all information on the device, applications should be encrypted as well. Just employing encryption for the data store is not sufficient. If the device is fully encrypted, then all apps would have to have access to the data, in essence bypassing the encryption from an app point of view. Apps with sensitive information should control access via their own set of protections. The only way to segregate data within the device is for apps to manage their own data stores through app-specific encryption. This will allow sensitive data to be protected from rogue applications that would leak data if uniform access was allowed.

## Transitive Trust/Authentication

Security across multiple domains/platforms is provided through trust relationships. When trust relationships between domains or platforms exist, authentication for each domain trusts the authentication for all other trusted domains. Thus, when an application is authenticated, its authentication is accepted by all other domains/platforms that trust the authenticating domain or platform. Trust relationships can be very complex in mobile devices, and often security aspects aren’t properly implemented. Mobile devices tend to be used across numerous systems, including business, personal, public, and private. This greatly expands the risk profile and opportunity for transitive trust-based attacks. As with all other applications, mobile applications should be carefully reviewed to ensure that trust relationships are secure.

## BYOD Concerns

BYOD has many advantages in business, and not just from the perspective of device cost. Users tend to prefer having a single device rather than carrying multiple devices. Users have less of a learning curve on devices they already have an interest in learning.

## Data Ownership

BYOD blurs the lines of data ownership because it blurs the lines of device management. If a company owns a smartphone issued to an employee, the company can repossess the phone upon employee termination. This practice may protect company data by keeping the company-issued devices in the hands of employees only. However, a company cannot rely on a simple factory reset before reissuing a device, because factory resetting may not remove all the data on the device. If a device is reissued, it is possible that some of the previous owner’s personal information, such as private contacts, still remains on the device. On the other hand, if the employee’s device is a personal device that has been used for business purposes, upon termination of the employee, it is likely that some company data remains on the phone despite the company’s best efforts to remove its data from the device. If that device is resold or recycled, the company’s data may remain on the device and be passed on to the subsequent owner. Keeping business data in separate MDM-managed containers is one method of dealing with this issue.

## Support Ownership

Support costs for mobile devices are an important consideration for corporations. Each device has its own implementation of various functions. While those functions typically are implemented against a specification, software implementations may not fully or properly implement the specification. This may result in increased support calls to your help desk or support organization. It is very difficult for a corporate help desk to be knowledgeable on all aspects of all possible devices that access a corporate network. For example, your support organization must be able to troubleshoot iPhones, Android devices, tablets, and so forth. These devices are updated frequently, new devices are released, and new capabilities are added on a regular basis. Your support organization will need viable knowledge base articles and job aids in order to provide sufficient support for the wide variety of ever-changing devices.

## Patch Management

Just as your corporate policy should enforce the prompt update of desktop and laptop computers to help eliminate security vulnerabilities on those platforms, it should also require mobile devices to be kept current with respect to patches. Having the latest applications, operating system, and so on is an important best defense against viruses, malware, and other threats. It is important to recognize that “jailbreaking” or “rooting” your device may remove the manufacturer’s security mechanisms and protection against malware and other threats. These devices may also no longer be able to update their applications or OS against known issues. Jailbreaking or rooting is also a method used to bypass security measures associated with the device manufacturer control, and in some locations, this can be illegal. Mobile devices that are jailbroken or rooted should not be trusted on your enterprise network or allowed to access sensitive data.

## Antivirus Management

Just like desktop and laptop computers, smartphones, tablets, and other mobile devices need protection against viruses and malware. It is important that corporate policy and personal usage keep operating systems and applications current. Antivirus and malware protection should be employed as widely as possible and kept up-to-date against current threats.

## Forensics

Mobile device forensics is a rapidly evolving and fast-changing field. Because devices are evolving so quickly and changing so fast, it is difficult to stay current in this field. Solid forensics principles should always be followed. Devices should be properly handled by using RF-shielded bags or containers. Because of the rapid changes in this area, it’s best to engage the help of trained forensics specialists to ensure data isn’t contaminated and the device state and memory are unaltered. If forensics are needed on a device that has both personal and business data, then policies need to be in place to cover the appropriate privacy protections on the personal side of the device.

## Privacy

When an employee uses his personal device to perform his work for the company, he may have strong expectations that privacy will be protected by the company. The company policy needs to consider this and address it explicitly. On company-owned devices, it’s quite acceptable for the company to reserve the right to access and wipe any company data on the device. The company can thus state that the user can have no expectation of privacy when using a company device. But when the device is a personal device, the user may feel stronger ownership. Expectations of privacy and data access on personal devices should be included in your company policy.

## On-boarding/Off-boarding

Most companies and individuals find it relatively easy to connect mobile devices to the corporate network. Often, there are no controls around connecting a device other than having a Microsoft Exchange account. When new employees join a company, the on-boarding processes need to include provisions for mobile device responsibilities. It is easy for new employees to bypass security measures if they are not part of the business process of on-boarding.

Employee termination needs to be modified to include termination of accounts on mobile devices. It’s not uncommon to find terminated employees with accounts or even company devices still connecting to the corporate network months after being terminated. E-mail accounts should be removed promptly as part of the employee termination policy and process. Mobile devices supplied by the company should be collected upon termination. BYOD equipment should have its access to corporate resources terminated as part of the off-boarding process. Regular audits for old or
