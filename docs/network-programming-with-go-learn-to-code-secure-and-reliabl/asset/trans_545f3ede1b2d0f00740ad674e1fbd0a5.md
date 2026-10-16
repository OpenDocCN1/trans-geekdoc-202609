
假设你的代理提交的证书需要确保它与你的代理通信，而不是受恶意行为者控制的证书。

你可以指示服务器仅与已认证的客户端建立 TLS 会话。这些客户端必须提交由受信任的证书颁发机构签名的证书，或是绑定到服务器的证书。在查看示例代码之前，客户端需要一个可以向服务器提交的证书以实现使用 TLS 进行安全通信的 **255** 认证。然而，客户端不能使用由 `$GOROOT/src/crypto/tls/generate_cert.go` 生成的证书进行客户端认证。相反，你需要创建自己的证书和私钥。

***生成用于认证的证书***

Go 的标准库包含所有你需要的功能，可以使用椭圆曲线数字签名算法（ECDSA）和 P-256 椭圆曲线生成自己的证书。图 11-12 展示了一个命令行实用程序的开头，用于完成此任务。在阅读时请记住，它可能不完全符合你的使用场景。例如，它生成 10 年的证书，并使用我的名称作为证书的主题，这在你的代码中可能不是你想要的（如果你真的想用，我很荣幸）。相应地进行修改即可。

```go
package main

import (

"crypto/ecdsa"

"crypto/elliptic"

"crypto/rand"

"crypto/x509"

"crypto/x509/pkix"

"encoding/pem"

"flag"

"log"

"math/big"

"net"

"os"

"strings"

"time"

)

var (

host = flag.String("host", "localhost",

"Certificate's comma-separated host names and IPs")

certFn = flag.String("cert", "cert.pem", "certificate file name") keyFn = flag.String("key", "key.pem", "private key file name")

)

func main() {

flag.Parse()

serial, err := rand.Int(rand.Reader, new(big.Int).Lsh(big.NewInt(1), 128))

if err != nil {

log.Fatal(err)

}

notBefore := time.Now()

template := x509.Certificate{

SerialNumber: serial,

**256** Chapter 11

Subject: pkix.Name{

Organization: \[\]string{"Adam Woodbeck"},

},

NotBefore: notBefore,

NotAfter: notBefore.Add(10 \* 356 \* 24 \* time.Hour),

KeyUsage: x509.KeyUsageKeyEncipherment |

x509.KeyUsageDigitalSignature |

x509.KeyUsageCertSign,

ExtKeyUsage: \[\]x509.ExtKeyUsage{

x509.ExtKeyUsageServerAuth,

2x509.ExtKeyUsageClientAuth,

},

BasicConstraintsValid: true,

IsCA: true,

}

*Listing 11-12: Creating an X.509 certificate template (* cert/generate .go *)* The command line utility accepts a comma-separated list of hostnames and IP addresses that will use the certificate. It also allows you to specify the certificate and private-key filenames, but it defaults to our familiar *cert.pem* and *key.pem* filenames.

The process of generating a certificate and a private key involves building a template in your code that you then encode to the X.509 format. Each certificate needs a serial number, which a certificate authority typically assigns. Since you’re generating your own self-signed certificate, you generate your own serial number using a cryptographically random, unsigned 128-bit integer. You then create an x509.Certificate object that represents an X.509-formatted certificate and set various values, such as the serial number, the certificate’s subject, the validity lifetime, and various usages for this certificate. Since you want to use this certificate for client authentication, you must include the x509.ExtKeyUsageClientAuth value.

If you omit this value, the server won’t be able to verify the certificate when presented by the client.

The template is almost ready. You just need to add the hostnames and IP addresses before generating the certificate (see Listing 11-13).

for \_, h := range strings.Split(*host, ",") {

if ip := net.ParseIP(h); ip != nil {

template.IPAddresses = append(template.IPAddresses, ip)

} else {

template.DNSNames = append(template.DNSNames, h)

}

}

priv, err := ecdsa.GenerateKey(elliptic.P256(), rand.Reader)

if err != nil {

log.Fatal(err)

}

Securing Communications with TLS **257**

der, err := x509.CreateCertificate(rand.Reader, &template, &template, &priv.PublicKey, priv)

if err != nil {

log.Fatal(err)

}

cert, err := os.Create(*certFn)

if err != nil {

log.Fatal(err)

}

err = pem.Encode(cert, &pem.Block{Type: "CERTIFICATE", Bytes: der}) if err != nil {

log.Fatal(err)

}

if err := cert.Close(); err != nil {

log.Fatal(err)

}

log.Println("wrote", *certFn)

}

*Listing 11-13: Writing the Privacy-Enhanced Mail (PEM)–encoded certificate*

*(* cert/generate .go *)*

You loop through the comma-separated list of hostnames and IP addresses, assigning each to its appropriate slice in the template. If the hostname is an IP address, you assign it to the IPAddresses slice. Otherwise, you assign the hostname to the DNSNames slice. Go’s TLS client uses these values to authenticate a server. For example, if the client connects to *https://www.google.com* but the common name or alternative names in the server’s certificate do not match *www.google.com*’s hostname or resolved IP address, the client fails to authenticate the server.

Next you generate a new ECDSA private key using the P-256 elliptic curve. At this point, you have everything you need to generate the certificate. The x509.CreateCertificate function accepts a source of entropy (crypto/rand’s Reader is ideal), the template for the new certificate, a parent certificate, a public key, and a corresponding private key. It then returns a slice of bytes containing the Distinguished Encoding Rules (DER)–encoded certificate. You use your template for the parent certificate since the resulting certificate signs itself. All that’s left to do is create a new file, generate a new pem.Block with the DER-encoded byte slice, and PEM-encode everything to the new file. You don’t have to concern yourself with the various encodings. Go is quite happy with using PEM-encoded certificates on disk.

Now that you have a new certificate on disk, let’s write the corresponding private key in Listing 11-14.

key, err := os.OpenFile(*keyFn, os.O_WRONLY|os.O_CREATE|os.O_TRUNC, 10600)

if err != nil {

log.Fatal(err)

}

privKey, err := x509.MarshalPKCS8PrivateKey(priv)

if err != nil {

log.Fatal(err)

}

err = pem.Encode(key, &pem.Block{Type: "EC PRIVATE KEY", Bytes: privKey})

if err != nil {

log.Fatal(err)

}

if err := key.Close(); err != nil {

log.Fatal(err)

}

log.Println("wrote", *keyFn)

}

*Listing 11-14: Writing the PEM-encoded private key (* cert/generate .go )*

Whereas the certificate is meant to be publicly shared, the private key is just that: private. You should take care to assign it minimal permissions.

Here, you’re giving only the user read-write access to the private-key file and removing access for everyone else. We marshal the private key into a byte slice and, similarly, assign it to a new pem.Block before writing the PEM-encoded output to the private-key file.

Listing 11-15 uses the preceding code to generate certificate and key pairs for the server and the client.

$ **go run cert/generate.go -cert serverCert.pem -key serverKey.pem -host localhost**

2006/01/02 15:04:05 wrote serverCert.pem

2006/01/02 15:04:05 wrote serverKey.pem

$ **go run cert/generate.go -cert clientCert.pem -key clientKey.pem -host localhost**

2006/01/02 15:04:05 wrote clientCert.pem

2006/01/02 15:04:05 wrote clientKey.pem

*Listing 11-15: Generating a certificate and private-key pair for the server and the client* Since the server binds to *localhost* and the client connects to the server from *localhost*, this value is appropriate for both the client and server certificates. If you want to move the client to a different hostname or bind the server to an IP address, for example, you’ll need to change the *host* flag accordingly.

***Implementing Mutual TLS***

