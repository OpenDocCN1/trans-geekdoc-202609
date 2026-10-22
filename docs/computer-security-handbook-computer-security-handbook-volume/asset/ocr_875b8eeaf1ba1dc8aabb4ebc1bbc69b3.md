# Exhibit 37.6 Trust Level Determination

| Category | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| Inconvenience or distress | Low | Med | High | High |
| Financial loss | Low | Med | Med | High |
| Harm to agency programs or public interests | N/A | Low | Med | High |
| Personal safety | N/A | N/A | Low | Med/high |
| Civil or criminal violations | N/A | Low | Med | High |
| Information classification |  |  |  |  |
| Confidentiality | Low | Med | High | High |
| Integrity | Low | Med | High | High |

Note: the trust level is sometimes confused with trust factors (something you have, something you know, something you know). A Smart Card may be a Level 3 (Medium, hardware) but part of a two factor (username, smartcard) authentication.

trust path from the trust anchor(s) of the relying party to the subscriber whose signature needs to be verified or to whom an encrypted message is to be sent.

# 37.6.1 Levels of Trust.

As referenced in Office of Manpower and Budget Memorandum OMB M04-04, Section 2.1, there are four basic levels of trust⁹:

+   - **Level 1.** Little or no confidence in the asserted identity’s validity
+   - **Level 2.** Some confidence in the asserted identity’s validity
+   - **Level 3.** High confidence in the asserted identity’s validity
+   - **Level 4.** Very high confidence in the asserted identity’s validity

Each level requires a different initial authentication of identity, and higher levels (or those used for classified information) require background investigations. Level 3 is also known as Medium Assurance and is divided into two forms: (1) software (certificates and keys can be exported and moved between devices) and (2) hardware (certificates may be exported but keys and cryptographic functions are performed on a specific hardware device [e.g., a smart card, USB token, or PC-Card device]). Most commercial PKI uses the equivalent of the Medium level of assurance.

Exhibit 37.6 shows one way to determine the required trust level as a function of threat of misuse.¹⁰

# 37.6.2 Proofing.

Each assurance level has a proofing (also known as vetting) requirement that increases with the trust level involved, as shown in Exhibit 37.7. Essentially none is required for level 1 (Basic) while extensive in-person requirements exist for level 4 (High).

# 37.6.3 Trusted Paths.

The trust model can be viewed as a chain, with its tail a certificate-issuing CA and its head the subscriber (i.e., the subject of the certificate). The subscriber can be another CA or an end entity. To ascertain the trustworthiness of a certificate, it is necessary to start with the relying party trust anchor and to follow in the direction of the chain until the subscriber (of interest to the relying party) is reached.