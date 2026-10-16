
-   [验证我是 `/woodbeck.net` 的合法所有者](https://wiki.example.org/feynmans_learning_method)。一旦确认，证书颁发机构会为 `/woodbeck.net` 签发新证书，并用其证书对其进行加密签名。我的服务器可以向客户端展示此证书，客户端通过验证证书颁发机构的签名来确认我是真实的 `/woodbeck.net` 而非冒充者。

-   证书颁发机构为 `/woodbeck.net` 签发签名证书的过程类似于美国政府签发我的护照。它们均由值得信赖的机构签发，证明其主体的真实性。就像美国信任爱尔兰一样，客户端仅在信任签发该证书的证书颁发机构时，才会信任 `/woodbeck.net` 证书。我可以像创建一份声称是我的护照的文件一样轻松创建自己的证书颁发机构并自签证书，但爱尔兰更倾向于承认杰克丹尼尔（Jack Daniel’s）的 Tennessee Whiskey 优于詹姆士（Jameson）的 Irish Whiskey，而且全世界没有任何操作系统或浏览器会信任我自签的证书。

***How to Compromise TLS***

-   2013 年 12 月 24 日，Google 发现土耳其的 Turktrust 证书颁发机构误发了一张证书，该证书允许恶意行为者冒充 `google.com`。这意味着攻击者可以欺骗你的浏览器，误以为正在通过 TLS 连接与 Google 通信，并诱导你泄露凭证。Google 迅速发现并采取措施解决此问题。

-   Turktrust 的失误削弱了其权威，损害了我们的信任。即使证书颁发机构运作正常，攻击者仍可能聚焦于个人而非服务器。如果攻击者能在你的操作系统受信任证书存储中安装其自身的 CA 证书，你的电脑将信任他签发的任何证书，这意味着他可以 compromise 所有你的 TLS 流量。

-   普通用户不会遭受此类特殊关注，攻击者更可能 compromise 服务器。一旦服务器被入侵，攻击者可以从内存中捕获所有 TLS 流量及对应的会话密钥。

-   虽然这些场景不常见，但必须意识到它们的可能性。总体而言，TLS 1.3 提供卓越的安全性，因其完整的握手签名、降级保护、前向保密和强加密而难以被攻击。

**244** 第 11 章

**传输中的数据保护**

确保你在网络上传输的数据完整性应是你的首要任务，无论是你自己的数据还是他人的数据。Go 让使用 TLS 变得如此简单，你几乎无法找到理由不使用它。在本节中，你将学习如何为客户端和服务器添加 TLS 支持，同时了解 TLS 如何在 TCP 上运行以及如何通过证书绑定来缓解恶意证书的威胁。

***客户端 TLS***

客户端在握手过程中主要关注通过其证书验证服务器的真实性。如果客户端无法信任服务器，则无法认为与服务器的通信是安全的。`net/http/httptest` 包提供了构造，能够轻松演示 Go 的 HTTP-over-TLS 支持（参见 Listing 11-1）。

package ch11

import (

"crypto/tls"

"net"

"net/http"

"net/http/httptest"

"strings"

"testing"

"time"

"golang.org/x/net/http2"

)

func TestClientTLS(t \*testing.T) {

ts := 1httptest.NewTLSServer(

http.HandlerFunc(

func(w http.ResponseWriter, r \*http.Request) {

if 2r.TLS == nil {

u := "https://" + r.Host + r.RequestURI

http.Redirect(w, r, u, http.StatusMovedPermanently)

return

}

w.WriteHeader(http.StatusOK)

},

),

)

defer ts.Close()

resp, err := 3ts.Client().Get(ts.URL)

if err != nil {

t.Fatal(err)

}

Securing Communications with TLS **245**

 if resp.StatusCode != http.StatusOK {

t.Errorf("expected status %d; actual status %d",

http.StatusOK, resp.StatusCode)

}

*Listing 11-1: Testing HTTPS client and server support (* tls\_client\_test .go *)* The httptest.NewTLSServer function returns an HTTPS server 1. Aside from the function name, this bit of code looks identical to our use of httptest i[n Chapter 8](#index_split_003.html#p187). Here, the httptest.NewTLSServer function handles the HTTPS server’s TLS configuration details, including the creation of a new certificate. No trusted authority signed this certificate, so no discerning HTTPS client would trust it. You’ll see how to work around this detail in just a moment by using a preconfigured client.

If the server receives the client’s request over HTTP, the request’s TLS field will be nil. You can check for this case 2 and redirect the client to the HTTPS endpoint accordingly.

For testing purposes, the server’s Client method 3 returns a new \*http Client that inherently trusts the server’s certificate. You can use this client to test TLS-specific code within your handlers.

Let’s see what happens in Listing 11-2 when you attempt to communicate with the same server by using a new client without inherent trust for the server’s certificate.

*\--snip--*

tp := &http.Transport{

TLSClientConfig: &tls.Config{

CurvePreferences: \[\]tls.CurveID{1tls.CurveP256},

MinVersion: tls.VersionTLS12,

},

}

err = 2http2.ConfigureTransport(tp)

if err != nil {

t.Fatal(err)

}

client2 := &http.Client{Transport: tp}

\_, err = client2.Get(ts.URL)

if err == nil || !strings.Contains(err.Error(),

"certificate signed by unknown authority") {

t.Fatalf("expected unknown authority error; actual: %q", err)

}

3 tp.TLSClientConfig.InsecureSkipVerify = true

resp, err = client2.Get(ts.URL)

if err != nil {

t.Fatal(err)

}

**246** 第 11 章

 if resp.StatusCode != http.StatusOK {

t.Errorf("expected status %d; actual status %d",

http.StatusOK, resp.StatusCode)

}

}

*Listing 11-2: Testing the HTTPS server with a discerning client (* tls\_client\_test .go *)* You override the default TLS configuration in your client’s transport by creating a new transport, defining its TLS configuration, and configuring http2 to use this transport. It’s good practice to restrict your client’s curve preference to the P-256 curve 1 and avoid the use of P-384 and P-521. P-256 is immune to timing attacks, whereas P-384 and P-521 are not. Also, your client will negotiate a minimum of TLS 1.2.

An *elliptic curve* is a plane curve in which all points along the curve satisfy the same polynomial equation. Whereas first-generation cryptography like RSA uses large prime numbers to derive keys, elliptic curve cryptog-raphy uses points along an elliptic curve for key generation. P-256, P-384, and P-521 are specific elliptic curves defined in the National Institute of Standards and Technology’s Digital Signature Standard. You can find more details in the Federal Information Processing Standards (FIPS) publication 186-4 ( *https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.186-4.pdf*).

Since your transport no longer relies on the default TLS configuration, the client no longer has inherent HTTP/2 support. You need to explicitly bless your transport with HTTP/2 support 2 if you want to use it. Of course, this test doesn’t rely on HTTP/2, but this implementation detail can trip you up if you’re unaware that overriding the transport’s TLS configuration removes HTTP/2 support.

Your client uses the operating system’s trusted certificate store because you don’t explicitly tell it which certificates to trust. The first call to the test server results in an error because your client doesn’t trust the server certificate’s signatory. You could work around this and configure your client’s transport to skip verification of the server’s certificate by set-
