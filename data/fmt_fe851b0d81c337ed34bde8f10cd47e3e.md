
```php
if ($valid === TRUE && $dataSaved === TRUE) {
  URL::redirect('/blog/edit');
}
```

你可以在不进行重定向的情况下调用 `edit` 方法：

```php
if ($valid === TRUE && $dataSaved === TRUE) {
  $this->_edit(1);
}
```

在这个示例中，`_edit()` 方法将是一个保护或私有方法，在不通过上一步的情况下无法从 URL 访问。如果你确实需要一个独立的端点（如果该目的地有多个入口点，则可能是这样），你需要验证正确的步骤已经执行。在会话变量中沿每个请求传递任何适当的数据（通常称为 flash 数据）通常是最安全的方法。

```php
if ($valid === TRUE && $dataSaved === TRUE) {
  Session::flash('blogValid', TRUE);
  URL::redirect('/blog/edit');
}
```

在你的 `edit` 端点中，你会验证这些传递的数据：

```php
public function edit($id)
{
  if (Session::get('blogValid') !== TRUE) {
    //again, this should be a proper error
    die('Not Authorized');
  }
}
```

### 混淆

你听过“通过模糊性实现安全” 这个术语吗？它很少真实，但在某些情况下是有帮助的。大多数应用程序使用每个表中的 `ID` 字段作为主键。该 ID 然后在整个系统中用于访问数据。

但是，有时你不想向用户暴露真实的 ID。可能你正在发布一个新产品，但不希望用户知道他们是第 13 个用户。可能你拥有公开数据，但不希望你的网站被爬虫轻易抓取。

在这种情况下，你可以将 `ID` 混淆为非递增的内容（例如 1, 2, 3...），但可以转换为你的 `ID` 字段。与其这样做：

```php
Route::get('/edit/{id}', function($id) {
  //id = 432134
  $post = $db->post()->where([
    'id' => $id
  ])->row();
});
```

你可以这样做：

```php
Route::get('/edit/{hash}', function($hash) {
  //hash = BaPjae
  $id = HashId::decrypt($hash);

  $post = $db->post()->where([
    'id' => $id
  ])->row();
});
```

在这个示例中，`HashId::decrypt()` 调用仅仅是从你的服务器获取预存的安全哈希并将其应用于传递的哈希以确定 `ID`。这也可以反过来调用生成哈希：

```php
$hash = HashId::encrypt(432134);
echo $hash; // 输出 BaPjae
```

自己编写这些哈希方法其实相当简单，但我建议使用经过测试的 [HashIDs](http://www.hashids.org/php/) 库。这些库不仅易于使用，而且在许多编程语言中都有良好的维护，以确保整个基础设施的互操作性。

在某些情况下，可以认为混淆是必要的，甚至在你的特定用例中可能是强制要求的。例如，我见过人们将模糊性作为 HIPAA 数据的额外保护。一个用例是要求将 HIPAA 敏感数据存储在单独的数据库中；在这种情况下这是一个三层服务器架构。Web 应用程序使用的主键存储在一个数据库中（带有非敏感数据），敏感数据存储在另一个中，而中间数据库存储关系。这种设计是为了确保即使任何一个数据库被破解，获得的数据也是匿名或非敏感的。

我要再次强调这一点，因为它极其重要：在大多数情况下，模糊性并不能保护你免受任何合法的攻击。你不应该依赖它来确保安全。它仅仅让事情变得稍微难找一点手段。

## 安全文件处理

回到我们最初的故事：如果你有提供给用户查看或下载的文档，你不能简单地对 `*.pdf` 文件设置访问控制。为什么呢？我知道你们会问这个问题。我是这里的叙述者，这倒很有帮助。

你需要做的是将文件存储在服务器上，使其无法从你的 Web 服务器访问。这里有一个推荐的目录结构示例：

```
application/
composer.json
composer.lock
htdocs/
    .htaccess
    assets/
    templates/
    index.php
    robots.txt
uploads/
workers/
```

`htdocs/` 是 Apache（或你正在使用的任何 Web 服务器）为域名服务的位置。`uploads/` 是你存储上传文档的地方。你也可以通过服务器的配置来实现。在 Apache 中，如果 `uploads` 目录位于 `htdocs` 树下，你可以对指向该目录的任何请求返回 404 错误。

在你的应用程序中实现这一点，你需要根据文档类型创建一个用于访问文档的端点。例如，你可能需要提供每月财务报表，但仅提供给“会计”组的用户。

在这里我们定义访问这些内容的端点。通过这个端点，我们将验证用户的访问级别、读取文件，最后使用适当的头部将其输出到浏览器。

```
 1 Route::get(
 2   '/accounting/statements/{year}/{month}',
 3   function($year, $month) {
 4 
5 	check user access
 6 	$userModel = new UserModel;
 7 	$user = $userModel->current();
 8 
9 	check to make sure the user is logged in
10 	//and a member of accounting
11 	if ($user === FALSE || in_array('accounting', $us\
12 er->groups) === FALSE) {
13 	  //please add a legit error message
14 	  die('Not Authorized');
15 	}
16 
17 	//the user has access, let's read the file
18 	$directory = __DIR__ . '../uploads/acct/stmnts/';
19 	$filename  = (int) substr($year, 0, 4)  .
20 	             (int) substr($month, 0, 2) .
21 	             '.pdf';
22 
23 	//error handling for invalid files
24 
25 	//open the file
26 	$fileHandle = fopen($directory . $filename, 'r');
27 
28 	//read the file and close it
29 	$fileContents = fread($fileHandle);
30 	fclose($fileHandle);
31 
32 	//send the appropriate headers
33 	header('Content-type: application/pdf');
34 	header('Content-Disposition: inline; filename="' \
35 . $filename . '"');
36 	header('Content-Length: ' . filesize($directory .\
37  $filename));
38 	header('Expires: 0');
39 	header('Cache-Control: must-revalidate');
40 	header('Pragma: public');
41 
42 	//echo the file contents to the browser
43 	echo $fileContents;
44 
45 });
```

这防止了不应该看到此文件的人访问它，因为它位于 Web 服务器之外，并且经过了适当控制的检查。

### 总结

我们涵盖了基本的身份验证、通过验证进行的妥当访问控制以及安全文件处理。我希望你在开发下一个想法时能发现这些有所帮助。继续读下去，因为我们还没有结束。记住，我说了结束了才算真的结束！

# 第 5 章 - 安全默认值、跨站脚本和其他常见的攻击手段

本章是你需要防御的攻击的合集，因此并不具有概括性。请试着忍你的失望。

## 永远不要信任你自己 - 使用安全默认

安全系统的核心概念之一是安全默认。只要可能（而且通常都是可能的），你就应该尽早定义变量、属性等，并赋予安全的默认值。安全默认意味着 `NULL`、空或 `FALSE` 状态。在确定逻辑时，默认值始终应该是失败。例如，在之前的身份验证中，我检查密码是否正确。如果失败，函数将执行针对非正结果的默认逻辑。

让我们来看一个表单验证的简单示例。

```
 1 Route::post('/signup', function()
 2 {
3   //check for valid form
4   if (Form::validate('signup') === TRUE) {
5     //process the form
6   }
7 
8   //the default logic is failure
9   die('Invalid Form Data');
10 });
```

## 永远不要信任动态类型。它不是你的朋友。

动态类型是新程序员喜爱的特性。动态类型意味着你不需要对类型那么挑剔；只要足够接近它就能工作。此的问题在于，它并不总是按照你预期的方式工作。

让我们来看一个 PHP 原生函数 `stripos()` 的经典示例。场景是你尝试找出短语 `I am the one who knocks` 中是否存在字母 `i`。

```
 1 $phrase = 'I am the one who knocks';
 2 
3 $letterExists = stripos($phrase, 'i');
 4 
5 if ($letterExists != FALSE) {
6   echo 'we should be here';
7   return TRUE;
8 }
9 
10 echo "we shouldn't be here, yet we are";
11 return FALSE;
```

`stripos()` 函数返回匹配项在字符串中的索引。由于 `i` 是字符串的第一个字母，`stripos()` 返回 `0`。由于动态类型，`!= FALSE` 等同于 `0`。现在我们使用 `!==` 来修复这个问题。

```
 1 $phrase = 'I am the one who knocks';
 2 
3 $letterExists = stripos($phrase, 'i');
 4 
5 if ($letterExists !== FALSE) {
6   echo 'we should be here';
7   return TRUE;
8 }
9
10 echo "we shouldn't be here, and we aren't";
```

显式检查的另一个不为人知的优势是性能。大多数情况下，显式检查会更快，因为它不需要类型转换。如果你对 PHP 的性能差异感兴趣，我建议查看 [http://www.phpbench.com/]。

## 跨站脚本

跨站脚本 (XSS) 是向目标网站注入恶意代码的过程。这可以通过多种方式实现，但最终结果是用户的浏览器在当前会话中以用户的身份运行未经代码。

### 非持久性 XSS

这是传统的 XSS 攻击类型。它涉及向站点注入数据并引导用户访问恶意内容。

假设你网站上的页面接收 `?page_num=2&per_page=50` 作为查询字符串参数。如果你不对这些参数进行转义，攻击者可以将其值改为恶意代码。这些代码可以将用户带到删除页面、在他们的浏览器中运行 JavaScript 或进行任何客户端攻击。

在注入恶意代码后，攻击者通过某种方式让用户访问页面。当用户到达时，应用程序将验证其有效的用户会话并执行恶意代码。用户甚至可能删除自己的账户！

### 持久性 XSS

持久性 XSS 攻击是永久存储在服务器上的攻击。例如，像 Facebook 这样的社交共享网站允许用户保存并向其他用户消息。攻击者可以将恶意代码存储在 Facebook 帖子中。如果 Facebook 在显示这些数据时没有对其进行适当转义，该代码就会被执行。因此，任何看到攻击者状态的人都会运行这段恶意代码。

### 攻击入口点

我刚刚提到了两个 XSS 攻击入口点的示例，但这些并不是唯一的。基本上，任何从用户那里获取输入并将其显示在 Web 页面上的地方都是攻击者利用你网站的机会。

务必考虑数据进入系统的 `all` 地方，而不仅仅是输入字段。例如，你可能允许用户上传图片，然后重新显示图像 XIFF 数据。也许你可能会解析从外部程序导出的各种数据的 CSV 文件。在任何你重新显示信息的地方，都需要进行保护。

## 如何保护自己

修复此问题并不困难。首先，永远不要直接从 URL 获取数据并将其回显到浏览器。来自其他来源（如你的数据库或上传的文件）的数据也是如此。为了保护自己，你只需要对进入数据库的数据进行转义，并对显示给用户的数据进行转义。

我们之前已经在第 1 章中讨论过正确的数据库转义，因此我们将重点放在数据显示上。PHP 通过内置函数 `htmlentities()` 使这变得非常简单。该函数将妥妥地处理大多数数据。

让我们看看实现后的样子。你的视图文件以前看起来是这样：

```

1 <h1>Title</h1>

2 

3 Hello <?=$name?>,

```

现在应用保护后，它看起来是这样：

```

1 <h1>Title</h1>

2 

3 Hello <?=htmlentities($name)?>

```

如果你想保持 DRY^(22)，你可能会将此抽象为视图辅助函数库。大多数框架已经将其包含在它们的视图或模板库中。

## 跨站请求伪造

跨站请求伪造（CSRF）基本上是 XSS 攻击的对面。XSS 是通过受信任的网站利用用户，而 CSRF 则是通过受信任的用户来利用网站。

这方面的例子是攻击者发送伪造邮件，其中包含一个删除博客文章、电子邮件或任何内容的链接。目标用户随后点击链接并到达删除页面。由于用户是具有有效会话的管理员，你的应用程序将按照请求删除记录。用户并不知道该链接将他们带到了哪里，而现在他们的账户在未经许可的情况下被删除了。这可不妙。

这也不非是一个文本链接；它通常附带在图像或按钮上。这听起来可能是一个很小的风险，因为大多数关键网站功能都位于等待 POST 数据的表单之后。但同样很容易地扩展到使用按钮或 JavaScript 来提交隐藏表单。

### 如何防止此类攻击

第一步是确保 GET 请求不执行任何更改数据的操作。任何对数据执行的操作都应该要求 `POST`、`PUT` 或 `DELETE` 请求。如果用户点击删除按钮，他们应该被带到一个用于确认操作的表单。如果需要通过 GET 执行更改数据的操作（可能是为了 RESTful API），你可以在查询字符串中要求一个唯一的令牌。在接下来的示例中，我们将使用 POST 数据，但在处理 GET 请求时相同的概念也适用；只需在查询字符串中设置令牌而不是在 POST 参数中设置即可。

现在你已经通过提交表单来处理数据操作，我们需要向表单中添加 CSRF 令牌。我们的 CSRF 令牌将是一个标准的 Nonce（一次性数字）。我们将生成一个随机令牌，将其存储在用户的会话中，然后将其作为隐藏字段添加到我们的表单中。一旦表单被 POST，我们就可以 CSRF 令牌与会话中的令牌进行对比以验证请求。

首先，我们将创建一个生成令牌的函数。这通常会被放置在可以全局调用的地方，也许作为路由过滤器、投票者或辅助函数库。

```

 1 //假设表单类的其他部分在这里

 2 

 3 static function generateCsrf()

 4 {

 5   $token = mcrypt_create_iv(

 6     16,

 7     MCRYPT_DEV_URANDOM

 8   );

 9 

10   Session::flash(

 11     'csrfToken',

 12     $token

 13   );

 14 

15   return $token;

16 }

```

注意，我们在这里使用了 session flash 数据。Flash 数据将存储在会话中，但在被销毁之前只能在一次请求中。大多数会话包装类都支持这个概念。这使得我们的令牌不会在多个请求中有效。

接下来，我们将在路由闭包中调用它，并将令牌传递给生成表单的视图：

```

1 Route::get('/signup', function()

2 {

3   $data['token'] = Form::generateCsrf();

4 

5   return View::render('signup.form', $data);

6 });

```

现在是我们的视图，`signup/form.php`

```

 1 <form method="POST" action="/signup">

 2 

 3   <label>

 4 	First Name:

 5 	<input type="text" name="first_name" />

 6   </label>

 7 

 8   <label>

 9 	Last Name:

10 	<input type="text" name="last_name" />

11   </label>

 12 

 13   <label>

 14 	Email:
```
