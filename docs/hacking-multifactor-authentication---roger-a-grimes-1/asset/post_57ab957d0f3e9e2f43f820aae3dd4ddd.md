
## 154 Hacking Multifactor Authentication

legitimate sites register the digital fingerprint of their legitimate TLS digital certificates in publicly accessible, trusted certificate logs—for example, with logs maintained by Google or some other well-trusted CAs. The idea is that if someone submits an additional TLS digital certificate for an already registered domain—with an existing, valid, trusted, not-expired digital certificate—the duplicate registration would be quickly noticed and evaluated.

Initially, I didn't like the idea of certificate transparency, and I even wrote a few articles against it. To me, and others, it was re-creating the protection we had with already existing certificate revocation lists (CRLs) that are already widely used and deployed by most CAs. But over time I've come to appreciate one certificate transparency's main arguments: that the existing CRL protection was not working well or timely enough. Although certificate transparency has its own issues (such as requiring legitimate websites to register their digital fingerprints in one or more public logs), it has proven itself by helping protect end users against rogue domains and certificates used in Level 4 attacks.

For more information on certificate transparency, see

- www.certificate-transparency.org
- en.wikipedia.org/wiki/Certificate_Transparency
- searchquery.target.com/news/4500253976/Certificate-Transparency-catches-bad-digital-certificates-from-Symantec

Channel binding, RFC 5056 (tools.iet.org/html/rfc5056) and 5929 (tools.iet.org/html/rfc5929), also uses digital fingerprint comparisons of digital certificates, like certificate transparency, but in a distinctly different way. Certificate transparency involves centralized databases, which everyone can connect to and use. Channel binding, on the other hand, is done locally on a device, OS, or authentication solution basis and uses distinctly different methods. Certificate transparency logs can contain millions of digital fingerprints. Local channel binding databases often just store the sites a user or their authentication solution have intentionally decided to trust, store, and use specifically with channel binding.

> NOTE there are three types of channel binding, but I'm only covering the most relevant type known as tls-server-endpoint.

Authentication solutions that support channel binding can have: 1) enabled by default, 2) turned off by default but recommended, or 3) simply offered as a option but not really recommended. For example, FIDO has channel binding enabled in their specification, although it is not enabled in most implementations (i.e., by browser vendors) because of some false-positive use scenarios and disagreement by the browser vendors on the ultimate solution.

## Chapter 6 Access Control Tokens

**NOTE** there are other similar technologies such as Online Certificate Status Protocol (OCSP) stapling, trust anchors, and key pinning that attempted to do similar things to certify transparency and channel binding. However, they never caught on as broadly, because they did not have the backing of Google, which controls much of the Internet and these protocols.

Level 5 MitM proxy attacks are the most sophisticated and difficult to detect. Either the attacker has been able to access the legitimate site's real digital certificate and copied it in its entirety, including the private key, or they otherwise have been able to duplicate it. These types of attacks are extremely rare. I've not heard of one being used with a fake website (although I know of several stolen or fraudulently duplicated digital certificates used to sign trojan malware).

These types of attacks, if they occurred, would be hard to prevent. The user wouldn't notice anything wrong since the website is a look-alike and is appearing to be at the correct domain with the legitimate certificate. Transparency and channel binding would not prevent the attack because both original and copied/duplicated digital certificates would have the same attack fingerprint.

All levels of MitM attacks could be mitigated by a defense known as token binding, RFC 8471 (tools.ietf.org/html/rfc8471), introduced in late 2018. Token binding involves tying a client's long-lived authentication token to the authentication instance or located on both the client and the legitimate site or service. Here is how it works: A user's authentication solution generates a unique public/private key for each website, providing the public key to the website and possession of the corresponding private key, on every future TLS connection to the server. The registration of the token to the site and of the site is a very difficult hurdle for attackers to overcome—the preregistration of shared secrets allows only the legitimate site and token to successfully authenticate. A few authentication standards, support token binding (fidoalliance.org/fido-technotes-channel-binding-and-fido), but like channel binding, it is not enabled by default in most use cases for the same reasons.

## Kevin Mitnick MFA Bypass Attack Demo

My friend and coworker Kevin Mitnick, the world's most famous hacker and KnowBe4's Chief Hacker Officer, demo this type of attack against MFA on a very popular website. You can see a video of Kevin demonstrating this method, which bypasses MFA authentication like it doesn't even care, at the following site: blog.knowbe4.com/heads

## 157 Accidental Token Leak

Sometimes people don't realize how important session information is and inadvertently leak it to others. It happens all the time when friends send links to each other with “You’ve got to check this!” For example, the original person copies and forwards a link they are watching, not realizing the link contains their session ID.

- 
- arica.com/information-technology/2019/12/hackrone-breaches-outside-customers-private-reports
- 3. 
- community.spicworks.com/topic/2265465-alienauth-otx-gives-away-zoom-share-file-and-other-urls
- 4. 
- 5. 
- 6. 
- 7. 
- 8. 
- 9. 
- 10. 
- 11. 
- 12. 
- 13. 
- 14. 
- 15. 
- 16. 
- 17. 
- 18. 
- 19. 
- 20. 
- 21. 
- 22. 
- 23. 
- 24. 
- 25. 
- 26. 
- 27. 
- 28. 
- 29. 
- 30. 
- 31. 
- 32. 
- 33. 
- 34. 
- 35. 
- 36. 
- 37. 
- 38. 
- 39. 
- 40. 
- 41. 
- 42. 
- 43. 
- 44. 
- 45. 
- 46. 
- 47. 
- 48. 
- 49. 
- 50. 
- 51. 
- 52. 
- 53. 
- 54. 
- 55. 
- 56. 
- 57. 
- 58. 
- 59. 
- 60. 
- 61. 
- 62. 
- 63. 
- 64. 
- 65. 
- 66. 
- 67. 
- 68. 
- 69. 
- 70. 
- 71. 
- 72. 
- 73. 
- 74. 
- 75. 
- 76. 
- 77. 
- 78. 
- 79. 
- 80. 
- 81. 
- 82. 
- 83. 
- 84. 
- 85. 
- 86. 
- 87. 
- 88. 
- 89. 
- 90. 
- 91. 
- 92. 
- 93. 
- 94. 
- 95. 
- 96. 
- 97. 
- 98. 
- 99. 
- 100. 
- 101. 
- 102. 
- 103. 
- 104. 
- 105. 
- 106. 
- 107. 
- 108. 
- 109. 
- 110. 
- 111. 
- 112. 
- 113. 
- 114. 
- 115. 
- 116. 
- 117. 
- 118. 
- 119. 
- 120. 
- 121. 
- 122. 
- 123. 
- 124. 
- 125. 
- 126. 
- 127. 
- 128. 
- 129. 
- 130. 
- 131. 
- 132. 
- 133. 
- 134. 
- 135. 
- 136. 
- 137. 
- 138. 
- 139. 
- 140. 
- 141. 
- 142. 
- 143. 
- 144. 
- 145. 
- 146. 
- 147. 
- 148. 
- 149. 
- 150. 
- 151. 
- 152. 
- 153. 
- 154. 
- 155. 
- 156. 
- 157. 
- 158. 
- 159. 
- 160. 
- 161. 
- 162. 
- 163. 
- 164. 
- 165. 
- 166. 
- 167. 
- 168. 
- 169. 
- 170. 
- 171. 
- 172. 
- 173. 
- 174. 
- 175. 
- 176. 
- 177. 
- 178. 
- 179. 
- 180. 
- 181. 
- 182. 
- 183. 
- 184. 
- 185. 
- 186. 
- 187. 
- 188. 
- 189. 
- 190. 
- 191. 
- 192. 
- 193. 
- 194. 
- 195. 
- 196. 
- 197. 
- 198. 
- 199. 
- 200. 

## Access Control Token Defenses

There are not many, if any, safeguards an end user can use to prevent the generation of insecure access tokens. At the most, buyers should ensure that any MFA solutions they choose include the defenses we will explore in this section. MFA developers can implement the defenses to prevent attackers from guessing, reproducing, and stealing access tokens.

# Generate Random, Unguestable Session IDs

The best and simplest defense is to generate random and unguestable session IDs. Always include some other randomly generated information that an attacker could not obtain or guess. Use a random process that is truly random (don’t build your own or rely on the “random” functions included with most programming or scripting languages that have not been tested and certified as truly random). If you are unsure how to create truly unique or random session IDs, connect with someone who has the appropriate knowledge and experience. Too many developers get this part wrong, and it can be embarrassing if you have to admit this sophomore mistake in a public advisory about the error.
