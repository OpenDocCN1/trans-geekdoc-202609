
## 74. PHPStan

PHPStan is a static analysis tool for PHP that focuses on finding errors in your code without actually running it. It can detect potential bugs and inconsistencies, adhering to modern development practices to ensure code reliability and maintainability. It supports various levels of analysis, from basic to strict, allowing developers to gradually improve their code base.

Ex:PHPStan

```php
// PHPStan is typically run from the command line, analyzing your
PHP files for potential issues. Here's an example command:
// $ vendor/bin/phpstan analyse src --level=max
// The command tells PHPStan to analyze the "src" directory of your
project at the maximum strictness level.
// Since PHPStan runs from the command line, here's a simplified PHP
example that might raise an error when analyzed by PHPStan:
function addNumbers(int $a, int $b): int {
    return $a + $b;
}
echo addNumbers('5', 10);
```

PHPStan would report a type mismatch error, indicating that a string is passed where an integer was expected, highlighting the line: Parameter #1 $a of function addNumbers expects int, string given.

PHPStan is a tool that helps improve the quality of your PHP code without having to execute it. To use PHPStan, you first need to install it via Composer with the command composer require --dev phpstan/phpstan. After installation, you can run it against your project's PHP files as shown in the example. PHPStan checks your code against a set of rules to identify potential issues, such as type mismatches, undefined variables, and more. The level of strictness can be adjusted, making it possible to start with basic checks and progress to more thorough analyses as your project evolves. This flexibility makes PHPStan an excellent choice for projects at any stage of development, from legacy codebases undergoing modernization to brand-new projects aiming for high-quality code from the start. The example provided demonstrates how PHPStan can catch common errors, such as type mismatches, that might not be immediately evident to the developer, especially in dynamically typed languages like PHP.

## 75. SwiftMailer

SwiftMailer is a library for sending emails from PHP applications. It provides a flexible and elegant object-oriented approach to sending emails with a multitude of features.

Ex:SwiftMailer

```php
require_once 'vendor/autoload.php';
// Create the Transport
$transport = (new Swift_SmtpTransport('smtp.example.com', 25))
->setUsername('your_username')
->setPassword('your_password');
// Create the Mailer using your created Transport
$mailer = new Swift_Mailer($transport);
// Create a message
$message = (new Swift_Message('Wonderful Subject'))
->setFrom(['john@doe.com' => 'John Doe'])
->setTo(['receiver@domain.org', 'other@domain.org' => 'A name'])
->setBody('Here is the message itself');
// Send the message
$result = $mailer->send($message);
?>
```

// The result will be an integer indicating the number of successful recipients. If everything is set up correctly, you'll see a positive number.

This example showcases how to send an email using SwiftMailer. First, you include the SwiftMailer library with require_once 'vendor/autoload.php';. Next, you create a "transport" that SwiftMailer will use to send the email. In this case, we're using SMTP with a fictional server smtp.example.com, and you provide your SMTP credentials. After setting up the transport, you create a "mailer" object that is responsible for sending the email. Then, you construct the email message itself using the Swift_Message class. This includes setting the sender and receiver addresses, the subject, and the body of the email. Finally, you send the email using the send method on the mailer object. The send method returns the number of successful recipients. If the setup is correct and the SMTP server accepts the email, this should be a positive number, indicating the email was sent successfully. SwiftMailer handles many complexities of email sending, such as MIME types and headers, making it a robust solution for PHP applications.

## 76. PHPExcel (Now PhpSpreadsheet)

PHPExcel, now known as PhpSpreadsheet, is a library for reading and writing spreadsheet files (Excel, LibreOffice, etc.). It supports various file formats including XLSX, XLS, and CSV, providing a way to interact with spreadsheet data programmatically.

Ex:PHPExcel (Now

```php
require 'vendor/autoload.php';
use PhpOffice\PhpSpreadsheet\Spreadsheet;
use PhpOffice\PhpSpreadsheet\Writer\Xlsx;
$spreadsheet = new Spreadsheet();
$sheet = $spreadsheet->getActiveSheet();
$sheet->setCellValue('A1', 'Hello World !');
$writer = new Xlsx($spreadsheet);
$writer->save('hello_world.xlsx');
?>
```

// A file named will be created with "Hello World !" in cell A1.

In this example, we demonstrate creating a simple Excel file using PhpSpreadsheet, the successor of PHPExcel. First, we include the

## 77. Whoops

Whoops is a PHP library designed to handle errors and exceptions in a more user-friendly manner. It provides a stack-based error handler that can be integrated into any PHP application, making it easier to debug during development. Whoops displays detailed diagnostic information, including the file and code line where the error occurred, the call stack, and, if available, the relevant code snippet.

Ex:Whoops

```php
require 'vendor/autoload.php';
$whoops = new \\Whoops\\Run;
$whoops->pushHandler(new \\Whoops\\Handler\\PrettyPageHandler);
$whoops->register();
throw new Exception("Something went wrong!");
```

A detailed error page showing the exception "Something went wrong!", the file and line number where the exception was thrown, the stack trace, and the relevant code snippet.

This code snippet demonstrates how to integrate Whoops into a PHP project to improve error handling. require 'vendor/autoload.php'; - This line includes the Composer autoloader, assuming Whoops has been installed via Composer. Composer is a dependency manager for PHP, used to install and manage libraries in a project. $whoops = new \\Whoops\\Run; - Creates an instance of the Whoops error handler. $whoops->pushHandler(new \\Whoops\\Handler\\PrettyPageHandler); - Adds a "pretty" error page handler to the Whoops stack. This handler is responsible for generating the user-friendly error pages. $whoops->register(); - Registers the Whoops instance as the default error handler for PHP, replacing the standard PHP error handler. throw new Exception("Something went wrong!"); - This line is just an example of throwing an exception to trigger Whoops. In a real application, exceptions might be thrown by the application code or PHP itself. When an error or exception occurs, Whoops takes over and displays a comprehensive error page with all the diagnostic information, significantly aiding the debugging process. It is particularly useful during development, as it provides much more context than PHP's default error reporting.

Composer autoloader to autoload the Predis library, assuming it has been installed via Composer. new Predis\Client([...]); - This line creates a new instance of a Predis client. The array passed to the constructor contains the connection parameters for the Redis server. In this example, it's connecting to Redis running on localhost (127.0.0.1) on the default port (6379). $client->set('foo', 'bar'); - Sets the value of the key foo to bar in Redis. This demonstrates how to write data to Redis using Predis. $value = $client->get('foo'); - Retrieves the value of the key foo from Redis, which should be bar as set in the previous step. echo $value; - Prints the value retrieved from Redis to the standard output. In this case, it prints bar. Predis abstracts the communication with Redis, providing a simple and intuitive API for PHP applications to leverage Redis's capabilities. It supports a wide range of Redis commands and features, making it a versatile choice for PHP developers working with Redis.
