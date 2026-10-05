
# 为安全 API 实现 JWT

JSON Web Tokens (`JWTs`) 是一种开放标准 (`RFC 7519`)，它定义了一种紧凑且自包含的方式，用于以 JSON 对象的形式在各方之间安全地传输信息。此信息可以被验证和信任，因为它是经过数字签名的。`JWTs` 可以使用密钥（使用 `HMAC` 算法）或使用 `RSA` 或 `ECDSA` 的公钥/私钥对进行签名。

## JWT 在安全 API 中的优势

* **紧凑性**：`JWTs` 紧凑，使其易于通过 URL、POST 参数或 HTTP 头部内部传输。
* **自包含**：`JWT` 包含有关用户的所有必要信息，避免了多次查询数据库的需求。
* **安全性**：令牌经过加密，提供两方之间的安全性；服务器可以验证令牌的真实性，以确保令牌发送者就是其声称的人。
* **跨域/平台**：`JWTs` 在不同域和平台上都很有用，增强了不同系统之间通信的灵活性。
* **性能**：使用 `JWT` 进行会话信息可减少服务器端会话数据的存储需求，这对于扩展应用程序尤其有益。

## 实现 JWT

要实现 `JWTs`，我们将使用 Go 包 `github.com/dgrijalva/jwt-go`，它提供了创建和验证 `JWTs` 所需的工具。

### 安装 JWT Go 包

首先，安装 JWT 包：
```
go get -u github.com/dgrijalva/jwt-go
```

### 创建 JWT 令牌

我们需要一个函数，在用户登录后生成 `JWT` 令牌。以下是您可能如何实现此功能的方式：

```go
package main
import (
"fmt"
"time"
"net/http"
"github.com/dgrijalva/jwt-go"
)
var mySigningKey = []byte("secret") // Ensure to keep this key safe
func GenerateJWT() (string, error) {
  token := jwt.New(jwt.SigningMethodHS256)
  claims := token.Claims.(jwt.MapClaims)
claims["authorized"] = true
claims["user_id"] = "123456"
claims["exp"] = time.Now().Add(time.Hour * 24).Unix() // Token expires after 24 hours
tokenString, err := token.SignedString(mySigningKey)
if err != nil {
  fmt.Errorf("Something Went Wrong: %s", err.Error())
return "", err
}
return tokenString, nil
}
```
在此代码中，我们创建一个新令牌，使用 HMAC SHA256 算法进行签名。我们包含诸如用户标识和过期时间之类的声明。

### 设置 HTTP 端点以使用 JWT

创建一个在被访问时签发令牌的端点：

```go
func homePage(w http.ResponseWriter, r *http.Request) {
validToken, err := GenerateJWT()
if err != nil {
  fmt.Fprintf(w, err.Error())
}
 fmt.Fprintf(w, validToken)
}
func handleRequests() {
http.HandleFunc("/", homePage)
 http.ListenAndServe(":9001", nil)
}
```

### 创建中间件以保护路由

为了利用 `JWT` 保护某些路由，您可以创建中间件来检查请求头中的有效令牌：

```go
func isAuthorized(endpoint func(http.ResponseWriter, *http.Request)) http.Handler {
return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
if r.Header["Token"] != nil {
token, err := jwt.Parse(r.Header["Token"][0], func(token *jwt.Token) (interface{}, error) {
if _, ok := token.Method.(*jwt.SigningMethodHMAC); !ok {
return nil, fmt.Errorf("There was an error")
}
return mySigningKey, nil
})
if err != nil {
  fmt.Fprintf(w, err.Error())
}
if token.Valid {
  endpoint(w, r)
}
} else {
  fmt.Fprintf(w, "Not Authorized")
}
})
}
func handleRequests() {
 http.Handle("/", isAuthorized(homePage))
 http.ListenAndServe(":9001", nil)
}
```
此中间件检查 `"Token"` 头并验证它。如果令牌有效，它将调用原始端点；如果无效，则返回 `"Not Authorized"` 响应。

总而言之，此配置使用户访问权限得到严格控制，提高了应用程序的安全性和性能，并使跨平台交互变得更容易。除了保护应用程序之外，该系统还提供了一种可扩展的方式来验证用户身份并管理其会话。
