This cycle continues from request to request throughout the remainder of the user’s session.

For the name for your cookie, you should stick with something easily identifiable such as `session_id`. The scope should be restricted to your own Web server (or, in a pinch, domain), and the validity equal to the maximum dwell time you think users will need on your site. For example, if you don’t think a typical user will ever use the site for more than half an hour, setting a validity period of 30 minutes isn’t a bad idea.

Historically, there has been controversy surrounding the privacy of the use of cookies. The bulk of that controversy has arisen from a mixture of the ignorance of those detractors, some instances of extraordinarily poor site design (often by agencies and brands that should know better), and perhaps some commercially unscrupulous site operators.

Despite the controversy, there is absolutely no reason for any user to fear a simple session identifier being issued through a cookie. However, do ensure that you restrict the scope of the cookie to your server and your server only, so that it is not inadvertently sent to any other sites that may attempt to use it for tracking purposes. In addition, it makes sense to post a clear and concise privacy policy on your Web site that explains to your users the purpose of the cookies you use, and the steps you have taken to safeguard users’ privacy and security.

In addition, remember that cookies should only be used to store session identifiers, and never any data associated with that session. Such data, held on your server, is properly secured and kept away from prying eyes. A session identifier is meaningless outside the context of your application, so it puts little at risk. It’s a bit like losing your house key. If you were dumb enough to attach a tag with your address to it, then you’d better get your locks changed pretty quickly. If you didn’t, you have nothing to worry about.

Despite all this, some potential pitfalls do exist, as the next section explains.

# Session Security

Is a session identifier really secure in itself? There are certainly a few risks associated with using session identifiers as the sole means of identifying logged-in users on your site, but, mercifully, there are countermeasures you can take to help minimize those risks.

# Guessing at Valid Sessions

If a malicious visitor to your site happens to fashion a valid session identifier, he or she can hijack the session of another visitor. After all, if user A is making request after request using session identifier X, and then malicious user B comes along and uses session identifier X to make a request as well, your Web site will assume that user B is user A, and user B will have access to everything user A has access to, potentially exposing sensitive information.

For this scenario to be realized, the potential hacker needs to guess at a valid session identifier. How feasible is doing so in a real-world situation?

Consider your 32-character hexadecimal string. This could be generated in any number of ways, but assume that it is largely random. With 32 bytes, and 16 possible characters for each byte (a through f, and 0 through 9), you have 16^32 possible combinations for your session identifier. That’s a big number — too