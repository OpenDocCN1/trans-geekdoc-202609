# Chapter 24 The Future of Authentication 501

Total cost of ownership of hardware MFA tokens is among the highest solutions in the MFA world and often requires additional training beyond a written document or online guide. Phone-based MFA solutions are often easily used and understood by users. There are three basic phone-based MFA models:

+   * Voice-authentication
* Phone app
* SMS-based

Phone apps are split into OTP methods, traditional MFA phone apps, and phone apps with without push notification. Phone-based TOTP, like that used with Google Authenticator and Microsoft Authenticator, is very popular, but it is likely to be seriously challenged in popularity by phone apps with push notification over the next few years.

# Wireless

Wireless MFA devices are the most common types already and this is not likely to change. MFA solutions requiring a wired connection to operate are mostly relegated to legacy products and scenarios.

# Changing/Morphing Standards

The authentication standards of my “youth,” from 20–30 years ago, are no longer around. Standards are usually a good thing, but they are constantly changing and morphing. They come and go over time. Eventually a new standard comes out that better addresses a growing need, and just like, today’s standard becomes tomorrow’s legacy protocol. Expect FIDO, OAuth, OpenID Connect, OATH, SAML, JSON, and all the other standards to be replaced by something else eventually.

# The Future

The authentication should not be a complete surprise to readers, as I’ve discussed it in previous chapters: zero trust and continuous, adaptive, risk-based authentication. These methods will be combined with ML/AI to create less friction. The user will be allowed to log on or automatically be logged in simply because the site/service are being accessed from a previously user-registered device. Not only the user’s device (be it a phone, car, TV, or other form factor) tied to the user, but the device or service also knows, from past experience, that the device is using the one they originate from. The user will be allowed to access an invalid site/service without having to log on their login to their originating device.

This already applies to large user populations today to browser-saved passwords and phone applications. Most phone apps don’t require authentication every time you want to use them. If already logged on successfully once, all you have to do each successive time is start the app (as long as it is from the same phone). Even my high-security bank app is fairly frictionless. When I start it, it’s