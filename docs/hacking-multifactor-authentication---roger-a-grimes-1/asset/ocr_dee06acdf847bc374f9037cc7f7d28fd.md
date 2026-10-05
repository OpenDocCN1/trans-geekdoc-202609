# Hacking Multifactor Authentication

progressively longer as each additional bad attempt is made. After too many bad attempts, the device should permanently lock itself and require a new device to be registered in order for the person to vote.

# Authentication and Operations

Because it is nearly impossible to display a full-sized election ballot nicely on a small-form device, our MFA solution requires that the MFA device be plugged into another computer that meets the communicated minimum requirements, whatever they may be. The voting ballot will be displayed on the voter's other device and screen, and the voter interacts with additional device to recover their choices.

When the MFA device is plugged into a computer—say, by USB cable—the MFA device should power up and do its hardware and software self-checks. Then the user should execute the MFA device's main program (however that is, depending on the operating system). This will launch a secure, very limited operating system and application, which is completely stored, contained, and loaded from the MFA device.

The user sees a voting application initialization message appear on the computer screen. The voter waits while the MFA device uses their existing Internet connection from the host device or a valid, supplied phone connection to check on updates and download any allowed, waiting online voting ballots. If updates are available, the device applies the updates and reboots. Upon rebooting, it checks again for both additional updates and voter ballots.

Updates and ballot downloads are encrypted with an asymmetric key that is specific to the MFA device being used so that only a particular ballot package, tied to voter and device, is allowed to be decrypted and installed on any particular MFA device. No other device or voter ID can use that particular ballot package, and it can run to completion only once. Incomplete voting requires that the whole process begin again with no previous choices shown or recorded.

Once updating and ballot downloading are finished, the device should confirm that it is securely communicating with the legitimate, expected voting device. If it is, the device should perform a challenge-response push to the device. Only the legitimate device and voter can generate the agreed-on challenge-response sequence. Verified, the MFA device should display a big, green OK on the MFA device's OLED. The software should allow the user to confirm that the big, green OK appears on the MFA device. If nothing is wrong with communications, or it's possible that the user's authentication experience on the computer's screen is simulated by a fake website. The user should be educated not to proceed with typing in their credentials or participating in voting or updating until the big, green OK appears on the MFA device. This, along with the preregistration of the device, should prevent authentication attacks from being successful.

> NOTE Of course, never underestimate the ability of users to ignore all signs of compromise and training no matter how well youve attempted to do.