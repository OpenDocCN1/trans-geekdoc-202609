# Chapter 19 API Abuses

Binance has an API (see binance-docs.github.io/apidocs/testnet/en/#general-api-information), which encourages users to get and use (cryptopro.app/help/binance-api-key) so that they can buy, sell, and trade cryptocurrencies very quickly. Binance API uses standards, REST and JSON, and is published and open. Binance’ API allowed it to become very popular, and quickly became one of the most used cryptocurrency APIs in the world. It is used for “trading bots,” which automated (high-frequency) trading based on predetermined entry and exit points. See an example of a trading bot that uses the Binance API here: thebitcoinnews.com/setting-up-api-keys-for-trading-bot-on-binance.

And when hackers took over Multiple Binance accounts using a socially engineered, fake proxy site, they used their knowledge of the API and the user’s stolen API keys (and Google Authenticator TOTP codes) to steal their cryptocurrency quite. As Binance CEO Changpeng wrote in his blog: “The hackers had the patience to wait, execute and well-orchestrated attacks through seemingly independent accounts at the most opportune time. That’s what having an API can assist with.

# Bypassing PayPal 2FA Using an API

Reported in 2014, this incident was a little aged but provides another example of how APIs can be used in bypassing MFA and of the slowness of some vendors to protect MFA security bugs. The bug was discovered by a single researcher and then reported to Duo Security (duo.com/blog/duo-security-researchers-uncover-bypass-of-paypal-s-two-factor-authentication), who got involved and thoroughly investigated.

PayPal has a RESTful API that uses OAuth and JSON. PayPal also allows MFA to be required to use their service, but at the time MFA did not work with PayPal’s mobile app. It was found that PayPal included in their OAuth message an indicator of whether the field was even named 2FA Enabled and possible values were True or False. Sniffing the connection between a participating client and PayPal’s service would have easily seen this.

> NOTE Discovery of this bug would have been delayed a bit if PayPal had not labeled the field 2FA Enabled.

So, all any attacker knowing victim’s login name and password would be to craft or intercept the authentication message headed to PayPal and change the 2FA Enabled value from True to False, and PayPal would take the user’s login name and password as valid credentials if the victim required 2FA. They also found an additional PayPal SOAP-enabled API that allowed them

To make matters worse, the original finder of this issue, Dan Saltman, reported this to PayPal via his official bug bounty program. For reasons not reported, PayPal did not report to Saltman over three weeks. In frustration, Saltman contacted Duo Security for their help, and got involved through the buggy program and assigned a case number. It still took PayPal another two