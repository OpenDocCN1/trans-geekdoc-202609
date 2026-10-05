# Chapter 23 Selecting the Right MFA Solution

**Table 23.7** Questions for OTP devices *(Continued*)

| Questions/requirements for OTP devices Answer |
| Do OTP code expire in a reasonable period of time? |
| Is OTP code replay prevented? |
| Is OTP code forcing prevented by account lockout or throttling? |
| How many bits is the seed value composed of? Anything below 128 bits is considered weak. |
| How is/seed value(s) communicated to the user? |
| If any setup codes (numbers, QR codes, etc.) are used for installs, do those codes expire and, if so, when? |
| If it's a software-based OTP, can the user have multiple identical instances running at once? |
| If it's a software-based OTP, can the user have multiple instances from locations? |
| Is Dynamic Symmetric Key Provisioning Protocol (DSKPP) used? |
| Where are seed values stored and how are they protected? |

# **Access Control Token Concerns

Most MFA devices involve access control tokens. Table 23.8 covers some of those concerns. Chapter 6, “Access Control Token Tricks,” for more details.

# **Biometric Questions

Table 23.9 lists some additional questions related to biometrics. Refer to Chapter 16, “Attacks Biometrics,” for more details.

**Table 23.8:** Questions concerning access control tokens

| Access control token questions Answers |
| Are access control tokens cryptographically protected? |
| Do access control tokens contain unique, randomly generated, unpredictable IDs? |
| Can MitM attacks be accomplished between a legitimate client and server? Can access tokens be intercepted and stolen by any MitM attack? |
| Does authentication only work with preregistered sites/services and MFA instances? |
| Do tokens expire in a reasonable amount of time? |
| Are there anti-replay mechanisms to prevent token replay? |
| Are access control tokens tied 1:1 to a specific identity? |