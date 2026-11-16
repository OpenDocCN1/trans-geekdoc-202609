```
tlsConfig := &tls.Config{
	CipherSuites: []uint16{
		tls.TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256,
		tls.TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384,
		tls.TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256,
		tls.TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384,
		tls.TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256,
		tls.TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256,
	},
}
```

**Important:** Restricting the supported cipher suites can mean that users with certain older browsers won't be able to use your website. There's a balance to be struck between security and backwards-compatibility, and the right decision for you will depend on the technology typically used by your user base. Mozilla's recommended configurations for modern, intermediate and old browsers may assist you in making a decision here.