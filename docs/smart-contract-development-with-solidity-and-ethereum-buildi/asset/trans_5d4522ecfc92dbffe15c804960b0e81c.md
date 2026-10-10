
理解哈希函数的另一种方式是将其视为为一段数据创建唯一的“指纹”。在 C# 中，生成数据块的哈希摘要非常容易。您可以使用多种算法，例如 MD5、SHA-1、SHA-256 和 SHA-512。哈希函数是单向函数。这意味着一旦对数据进行哈希处理，就无法将其还原为原始数据。相反，加密被设计为双向操作。使用密钥加密数据后，您可以使用相同的密钥反向操作并解密数据。

![](images/Figure_1.2.3.jpg)

**图 1.2.3**

对数据进行哈希处理时，除非原始数据以某种方式发生变化，否则每次操作生成的哈希值都相同。即使数据仅改变一位，生成的哈希代码也会完全不同。这使得哈希成为检查数据完整性的完美机制。当您想要通过网络将数据发送给另一个接收者时，这非常有用。在发送数据之前，您计算原始数据的哈希值以获取其唯一指纹。然后您将数据和哈希值发送给接收者。他们随后重新计算刚刚收到的原始数据的哈希值，并将其与您发送的哈希值进行比较。如果哈希代码相同，则数据已成功接收，没有任何数据丢失或损坏。如果哈希代码不匹配，则接收到的数据与最初发送的数据不同，您不应信任该数据。最常用的两种哈希方法是 MD5 和 SHA 系列哈希（SHA-1、SHA-256 和 SHA-512）。MD5 如今通常不再用于新软件，但如果您要与仍在使用 MD5 哈希的旧系统集成，它仍然具有相关性。本章我们将重点关注 SHA。

# SHA

SHA 系列是由美国国家标准技术研究院 (NIST) 发布的一系列加密哈希函数。SHA 系列涵盖了一些不同的变体，包括 SHA-1，这是一种 160 位的哈希函数，类似于早期的 MD5 算法。它由美国国家安全局设计，旨在成为数字签名算法的一部分。在 SHA-1 中发现了加密弱点，因此该标准在 2010 年后不再被批准用于大多数加密用途。接下来是 SHA-2，这是一个包含两个具有不同块大小的相似哈希函数的系列，称为 SHA-256 和 SHA-512。它们的字长不同。SHA-256 使用 32 位字，而 SHA-512 使用 64 位字。这些版本的 SHA 算法也由美国国家安全局设计。最后是 SHA-3，这是一种正式称为 `Keccak` 的哈希函数，于 2012 年在非国家安全局设计师的公开竞赛中被选中。它支持与 SHA-2 相同的哈希长度，其内部结构与 SHA 系列的其余部分有显著差异。将安全哈希实现到您的应用程序中是一个非常直接的过程。

.NET 框架在 `System.Security.Cryptography` 命名空间及其类中提供了封装的加密相关功能。`HashAlgorithm` 类是哈希算法的基类，包括 MD5、RIPEMD-160、SHA-1、SHA-256、SHA-384 和 SHA512。

`HashAlgorithm` 的 `ComputeHash` 方法用于计算哈希。它接受字节数组或流作为输入，并以 256 位字节数组的形式返回哈希值。

以下是 C# 中演示如何计算 SHA 哈希的简单控制台应用程序代码。

```csharp
using System;
using System.Text;
using System.Security.Cryptography;

namespace Cryptography
{
    class Program
    {
        static void Main(string[] args)
        {
            string input = "Blockchain";
            Console.WriteLine("Raw data: {0}", input);
            string hashedData = ComputeSha256Hash(input);
            Console.WriteLine("Hash {0}", hashedData);
            Console.WriteLine(ComputeSha256Hash("Blockchain"));
            Console.ReadLine();
        }

        static string ComputeSha256Hash(string rawData)
        {
            // Create a SHA256
            using (SHA256 sha256Hash = SHA256.Create())
            {
                // ComputeHash - returns byte array
                byte[] bytes = sha256Hash.ComputeHash(Encoding.UTF8.GetBytes(rawData));
                // Convert byte array to a string
                StringBuilder builder = new StringBuilder();
                for (int i = 0; i < bytes.Length; i++)
                {
                    builder.Append(bytes[i].ToString("x2"));
                }
                return builder.ToString();
            }
        }
    }
}
```

上述代码包含一个 `Main()` 方法，它是控制台应用程序的入口点。`Main()` 方法将输入设置为字符串 "Blockchain"，存储在名为 `input` 的变量中。然后调用一个名为 `ComputeSha256Hash()` 的方法，该方法定义在 `Main()` 方法下方，负责将输入字符串转换为哈希值。该方法创建 `SHA256` 类的实例并调用 `ComputeHash()` 方法，接受输入的字节数组并计算哈希值，然后将其返回给调用者方法 `Main()`。哈希创建后，该方法再次被调用以检查哈希是否再次计算相同或不同。我们看到哈希再次相同。下图显示了输出。

![](images/Figure_1.2.4.jpg)

**图 1.2.4**

# 认证哈希 (HMAC)

我们可以在 SHA-256 哈希的基础上更进一步，创建所谓的 `hashed message authentication` 代码。从根本上说，这与哈希相同，但更进一步。如果将单向函数（如 SHA-256）与秘密加密密钥相结合，则会得到所谓的哈希消息认证代码，简称 `HMAC`。与哈希代码一样，当您想要验证消息的完整性时，会使用 HMAC。HMAC 还允许您验证该消息的真实性，因为只有知道密钥的人才能计算出该消息的相同哈希值。HMAC 可以与不同的哈希函数一起使用，如 MD5 或 SHA 系列算法。HMAC 的加密强度取决于所用密钥的大小。在本课程中，我们将使用带有 256 位或 32 字节密钥的 HMAC。当您需要同时检查消息的完整性和真实性时，会使用哈希消息认证代码。

![](images/Figure_1.2.5.jpg)

**图 1.2.5**

例如，考虑这样一种场景：您收到一段数据及其哈希值。您可以通过重新计算该消息的哈希值并将其与收到的原始哈希值进行比较来验证消息的完整性；但是，您无法确定该消息和哈希值是否由您认识或信任的人发送。如果您使用哈希消息认证代码，您可以使用只有您和受信任的第三方知道的秘密密钥重新计算 HMAC，并将其与刚收到的 HMAC 进行比较。这起到了认证的作用。

在下面的示例中，我将向您展示如何使用带有 32 字节或 256 位密钥且基于 SHA-256 哈希算法的 HMAC。除了基于 SHA-256 的哈希 MAC，您还可以使用 SHA-1、SHA-512 和基于 MD5 的 SHA。接口都是相同的，但本课程我们将只使用 SHA-256 变体。

```csharp
using System;
using System.Text;
using System.Security.Cryptography;

namespace Cryptography
{
    class Program
    {
        static void Main(string[] args)
        {
            string input = "Blockchain";
            string key = "SecretKey";
            string hashedData = GetHash(input, key);
            Console.WriteLine("Hash {0}", hashedData);
            Console.ReadLine();
        }

        public static string GetHash(string toBeHashed, string key)
        {
            var keyToUse = Encoding.UTF8.GetBytes(key);
            var message = Encoding.UTF8.GetBytes(toBeHashed);
            using (var hmac = new HMACSHA256(keyToUse))
            {
                return Convert.ToBase64String(hmac.ComputeHash(message));
            }
        }
    }
}
```
