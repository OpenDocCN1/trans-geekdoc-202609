
关于数值类型，有几件事需要记住：

- 在 XSD 中，数字零 (0) 既不是负数也不是正数。因此 `positiveInteger` 从零开始，而 `nonNegativeInteger` 听起来像是同一回事，但实际上从一 (1) 开始。
- `Byte`、`short`、`int` 和 `long`（以及它们的无符号对应类型）受大小限制。`byte` 是能容纳在 8 位中的最大整数；`short` 为 16 位；`int` 为 32 位；`long` 为 64 位。
- 无符号 `byte` 的最大值是 2⁸−1 或 255。有符号变体使用最高位来指示变量是正数还是负数，因此损失了一位，但获得了表示负数的能力。有符号字节的范围从 −127 到 +127。

另外的数据类型有 `boolean`、`base64Binary` 和 `hexBinary`。这里没有涵盖几种其他字符串类型，因为它们在 SOAP 请求中很少使用。然而，在使用 XSD 定义任意文档时，它们可能会派上用场。只要不要忘记像这样在类型前面加上命名空间：`xsd:boolean`。

## 定义消息

现在数据类型/模式已定义，是时候指定消息了。在 WSDL 2.0 中，messages 元素不再存在，而是直接引用模式。1.1 规范要复杂得多。

消息定义了请求和响应所需的各个部分。在 RPC 的上下文中，将其视为参数列表和响应可能会有所帮助。或者，你也可以把消息想象成放入信封中的内容。仅需四种消息类型即可处理本节中的所有公司示例：

```xml
<message name="CompanyInputOutput">
  <part name="id" type="xsd:integer"/>
  <part name="company" type="tns:company"/>
</message>

<message name="ReferenceCompanyInput">
  <part name="id" type="xsd:integer"/>
</message>

<message name="CreateCompanyInput">
  <part name="company" type="tns:company"/>
</message>

<message name="DeleteCompanyOutput">
  <part name="result" type="xsd:boolean"/>
</message>
```

还记得本章前面定义的自定义复杂类型吗？它在这里的前两个消息定义中使用。

删除和检索操作使用相同的输入，因此它们只需要一个消息。同样地，创建和编辑公司都使用相同的输出格式。

## 指定端口

一旦消息定义完成，就该指定端口了。端口以它们生成或消费的消息类型来定义输入和输出，因此它们就是函数定义。常用的两种操作类型是单向和请求-响应。公司 WSDL 文件中定义的所有函数都是请求-响应，尽管单向函数只需排除“output”标签。

由于所有函数都有些相似，列出每个函数是不必要的。示例代码中的完整 WSDL 文件已定义了每个端口（函数）。GetCompany 端口的定义如下：

```xml
<portType name="CompanyPortType">
    <operation name="GetCompany">
        <input message="tns:ReferenceCompanyInput"/>
        <output message="tns:CompanyInputOutput"/>
    </operation>
</portType>
```

在单个端口内部定义多个操作是可能且可取的。然而，请记住端口类型接下来将用作绑定中的 type 属性，而每个绑定只能有一个类型。

## 定义绑定

下一步是定义绑定。在此过程中，请记住 HTTP 并不是 SOAP 传输的唯一协议，因此第一步是定义绑定的传输类型和样式。本章中的示例都使用 RPC 样式，这是最常见的：

```xml
<binding name="CompanyBinding" type="tns:CompanyPortType">
    <soap:binding style="rpc" transport="http://schemas.xmlsoap.org/soap/http" />
    <operation name="GetCompany">
        <soap:operation soapAction="http://example.com/GetCompany" />
        <input><soap:body use="literal"/></input>
        <output><soap:body use="literal"/></output>
    </operation>
</binding>
```

binding 标签的 soapAction 属性是 SOAP 世界中最令人困惑的属性之一，因为它看起来完全是多余的。毕竟，操作的类型在 SOAP 请求的主体中指定。为了更好地说明，这里是使用前面绑定发出的请求（头部包含在顶部）：

```
Content-Type: text/xml
Soapaction: http://example.com/GetCompany
Host: example.com
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"

<soap:Body>
    <companies:GetCompany xmlns:companies="http://example.com/companies">
        <id xsi:type="xsd:integer"></id>
    </companies:GetCompany>
</soap:Body>
</soap:Envelope>
```

两个加粗的区域都指示正在执行的操作。事实上，PHP SOAP 扩展会忽略 soap-action 头部。同样地，除非传输协议是 HTTP，否则 soap-action 不会被使用。那它为什么存在呢？有三个原因：

> 可以以更 RESTful 的方式使用 SOAP，而不一定将操作放在主体中。
> HTTP 头部可以被网络设备读取并用于优化（负载均衡、缓存等）。基于头部进行读取和过滤比解析 SOAP 请求要容易得多。
> 操作也可以包含在 Web 服务器日志中。在 Apache 中使用 CustomLog 指令即可做到这一点。例如：CustomLog logs/soap_log "%t %f $a > %{Soapaction}i"。

soap-action 必须原样传递给客户端。虽然它采用 URI 的形式，但不要求可解析。客户端不应尝试以任何方式转换操作。这包括但不限于将相对 URN 扩展为完全限定形式。

## 定义端点

创建 WSDL 的最后一步是定义服务。你可以使用服务来分组相似的功能或为服务定义端点。与 soap-action 不同，服务的端点必须是有效的 URI，因为客户端使用它进行连接。

```xml
<service name="CompanyService">
    <port name="CompanyPort" binding="tns:CompanyBinding">
        <soap:address location="http://example.com/companies/"/>
    </port>
</service>
```

通过结合前面六节中解释的所有内容，可以制作一个有效的 WSDL 1.1 文件，任何 SOAP 客户端都可以读取。

## 设置 SOAP 服务器

一旦有了 WSDL，使用 SOAP 库在 PHP 中设置 SOAP 服务器非常容易。事实上，第一次创建 WSDL 看起来可能比在 PHP 中实际实现过程调用更费力。

创建 SOAP 服务器有两种方法。两者都需要创建一个新的 PHP 文件（与端点在同一位置）并初始化一个新的服务器对象。一种是面向对象的，另一种是过程式的。为了处理遗留系统，先详细说明过程式方法。GetCompany 函数的过程式代码如下所示：

```php
<?php
$server = new SoapServer('company.wsdl');

$companyConnection = mysql_connect("localhost", "username", "password");
mysql_select_db("companies", $companyConnection);

function GetCompany( $id ) {
    global $companyConnection;

    $res = mysql_query("SELECT * FROM `companies` WHERE `id`=".(int)$id,
                        $companyConnection);

    if ( $row = mysql_fetch_assoc($res) ) {
        $company = new Company();
        $company->name = $row["name"];
        $company->website = $row["website"];

        return array( $id, $company );

    } else {
        throw new SoapFault("Server", "Company not found.");
    }
}

$server->addFunction("GetCompany");
$server->handle();
?>
```

最后的 handle() 调用实际上处理 SOAP 请求。它完成了读取标准输入和 HTTP 头部的繁琐工作。代码在找不到公司时也会抛出 SoapFault 异常。SoapFault 类继承自 Exception，因此可以像其他任何类型的异常一样使用。

当然，最好是创建一个类来处理过程调用。这样可以清理主变量作用域，使代码更易读。幸运的是，PHP SOAP 扩展提供了一种注册类的方法。然后类中的每个公共方法都会自动添加到接口中。私有和受保护的方法保持私有和受保护。新面向对象的代码如下所示：

```php
<?php
$server = new SoapServer('company.wsdl');

class CompanySoap {

    protected function _getDatabase() {
        static $conn = false;
        if ( $conn === false ) {
            $conn = mysql_connect("localhost", "username", "password");
```
