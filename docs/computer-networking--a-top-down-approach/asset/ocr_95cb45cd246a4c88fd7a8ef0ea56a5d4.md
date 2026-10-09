![](bbox=[0.28, 0.09, 0.85, 0.42])

Figure 8.14 ♦ Bob has his public key certified by the CA

| Field Name | Description |
| :--- | :--- |
| Version | Version number of X.509 specification |
| Serial number | CA-issued unique identifier for a certificate |
| Signature | Specifies the algorithm used by CA to sign this certificate |
| Issuer name | Identity of CA issuing this certificate, in distinguished name (DN) [RFC 4514] format |
| Validity period | Start and end of period of validity for certificate |
| Subject name | Identity of entity whose public key is associated with this certificate, in DN format |
| Subject public key | The subject’s public key as well indication of the public key algorithm (and algorithm parameters) to be used with this key |

Table 8.4 ♦ Selected fields in an X.509 and RFC 1422 public key

# 8.4 End-Point Authentication

End-point authentication is the process of one entity proving its identity to another entity over a computer network, for example, a user proving its identity to an e-mail server. As humans, we authenticate each other in many ways: We recognize each other’s faces when we meet, we recognize each other’s voices on the telephone, we are authenticated by the customs official who checks us against the picture on our passport.