
```
{
    if (empty($local_part)) { return false; }

    $bit_array = preg_split('/\\./',$local_part);
    while (list(,$bit) = each($bit_array))
    {
        if (!is_word($bit)) { return false; }
    }
    return true;
}

#word      = atom / quoted-string
#quoted-string = "<>" *(qtext/quoted-pair) "<>"; Regular qtext or
#                                   ;  quoted chars.
#qtext      = <any CHAR excepting "<>">.
#               "\" & CR, and including
#               linear-white-space>
#quoted-pair = "\" CHAR                 ; may quote any char
function is_word ( $word = "")
{
    if (preg_match('/^".*"$/i',$word))
    {
        return(is_quoted_string($word));
    }
    return(is_atom($word));
}

function is_quoted_string ( $word = "")
{
    $word = preg_replace('/^"/','',$word);   # remove leading quote
    $word = preg_replace('/"$/','',$word);   # remove trailing quote
    $word = preg_replace('/\\\+/','',$word);   # remove any quoted-pairs
    if (preg_match('/"\\|\r/',$word))   # if ", \ or CR, it's bad qtext
    {
        return false;
    }
    return true;
}

#atom      = 1*<any CHAR except specials, SPACE and CTLs>
#specials  = "(" / ")" / "<" / ">" / "@"  ; Must be in quoted-
#          / "," / ";" / ":" / "\" / "<>"  ; string, to use
#          / "." / "[" / "]"               ; within a word.
#SPACE     = <ASCII SP, space>            ; (     40,     32.)
#CTL       = <any ASCII control           ; ( 0- 37,  0.- 31.)
#           character and DEL>            ; (   177,    127.)
function is_atom ( $atom = "")
{
    
    if (
        (preg_match('/[\(\)<>@\,;\:\\\"\.\[\]]/',$atom))  # specials
            || (preg_match('/\040/',$atom))            # SPACE
            || (preg_match('/[\x00-\x1F]/',$atom))     # CTLs
    )
    {
        return false;
    }
    return true;
}

#domain    = sub-domain *("." sub-domain)
#sub-domain = domain-ref / domain-literal
#domain-ref = atom                        ; symbolic reference
function is_domain ( $domain = "")
{
    
    if (empty($domain)) { return false; }
    
# this is not strictly required, but is 99% likely sign of a bad domain
    if (!preg_match('/\./',$domain)) { return false; }
    
    $dbit_array = preg_split('/\./',$domain);
    while (list(,$dbit) = each($dbit_array))
    {
        if (!is_sub_domain($dbit)) { return false; }
    }
    return true;
}
function is_sub_domain ( $subd = "")
{
    
    if (preg_match('/^\[.*\]$/',$subd))   #domain-literal
    {
return(is_domain_literal($subd));
}
    return(is_atom($subd));
}
#domain-literal = "["*(dtext / quoted-pair) "]"
#dtext          = <any CHAR excluding "[".      ; => may be folded
#                " ]", "\" & CR, & including
#                linear-white-space>
#quoted-pair = "\" CHAR                     ; may quote any char
function is_domain_literal ( $dom = "")
{
    $dom = preg_replace('/\\/+/','',$dom);          # remove quoted pairs
    if (preg_match('/[\[\]\\\r]/',$dom))    # bad dtext characters
    {
        return false;
    }
    return true;
}
?>
```
你可能希望将所有这些函数放在一个文件中，然后在需要时包含它。它返回 1（表示 true）或空（表示 false）。你可能希望像这样使用它：

```
if ( !validate_email("myaddress@mydomain.com") )
{
    echo "this is not a valid email";
}
```

## 信用卡验证

以下是我们在第 14 章中使用的信用卡验证器。你可以在 /book/cart/ccval.php 中找到它。

```
/*
****************************************************************
* CCVal - Credit Card Validation function.
* 
* Copyright (c) 1999 Holotech Enterprises. All rights reserved.
* You may freely modify and use this function for
* your own purposes. You may freely distribute it, without
* modification and with this notice and entire header intact.
* This function accepts a credit card number and, optionally,
* a code for a credit card name. If a Name code is specified,
* the number is checked against card-specific criteria, then
* validated with the Luhn Mod 10 formula. Otherwise it is only
* checked against the formula. Valid name codes are:
*
*     mcd - Master Card
*     vis - Visa
*     amx - American Express
*     dsc - Discover
*     dnc - Diners Club
*     jcb - JCB
*
* A description of the criteria used in this function
* can be found at
* http://www.beachnet.com/~hstiles/cardtype.html.
* If you have any
* questions or comments, please direct them to
* ccval@holotech.net
*
*                                           Alan Little
*                                           Holotech Enterprises
*                                           http://www.holotech.net/
*                                           September 1999
*
*******************************************************************
/
function CCVal($Num, $Name = 'n/a')
{
    // You can't get money from an empty card
    if (empty($Num)) { return FALSE; }

    // Innocent until proven guilty
    $GoodCard = TRUE;
    //print "<h4>pre-code: GoodCard is ".($GoodCard ? "TRUE" :
    //"FALSE")."</h4>\n";

    // Get rid of any non-digits
    $Num = ereg_replace("[^[:digit:]]", "", $Num);

    // Perform card-specific checks, if applicable
    switch ($Name)
    {
case "mcd" :
    $GoodCard = ereg("^5[1-5].{14}$", $Num);
    break;

case "vis" :
    $GoodCard = ereg("^4.{15}$|^4.{12}$", $Num);
    break;

case "amx" :
    $GoodCard = ereg("^3[47].{13}$", $Num);
    break;

case "dsc" :
    $GoodCard = ereg("^6011.{12}$", $Num);
    break;

case "dnc" :
    $GoodCard = ereg("^30[0-5].{11}$|^3[68].{12}$", $Num);
    break;

case "jcb" :
    $GoodCard = ereg("^3.{15}$|^2131|1800.{11}$", $Num);
    break;
}
//print "<h4>pre-luhn: GoodCard is ".($GoodCard ? "TRUE" :
"FALSE")."</h4>\n";

//  The Luhn formula works right to left, so reverse the number.
$Num = strrev($Num);

$Total = 0;

for ($x=0; $x<strlen($Num); $x++)
{
$digit = substr($Num,$x,1);

//    If it's an odd digit, double it
    if ($x/2 != floor($x/2))
    {
        $digit *= 2;
    }

//    If the result is two digits, add them
    if (strlen($digit) == 2)
    {
        $digit = substr($digit,0,1) + substr($digit,1,1);
    }
}

//  Add the current digit, doubled and added if applicable, to the Total

$Total += $digit;
}

//  If it passed (or bypassed) the card-specific check and the Total is
//  evenly divisible by 10, it's cool!
//print "<h4>post-luhn: Total = $Total</h4>\n";

if ($GoodCard && $Total % 10 == 0) return TRUE; else return FALSE;
}
```

## recurse_directory

我写了以下代码来帮助我查看 Web 服务器上安装的所有文档。它将打印每个文档并提供这些文档的链接。

```
function recurse_directory($path="")
{
    global $DOCUMENT_ROOT, $HTTP_HOST
    if (empty($path)) {$path = $DOCUMENT_ROOT;}
    if(!is_dir($path))
    {
        return FALSE;
    }

    $dir = opendir($path);
    echo "<ul>";
    while ($file = readdir($dir))
    {
        if ($file != "." && $file != "..")
        {
            if (is_dir($path . "/" .$file))
            {
echo "<li><b>$file</b></li>";
    recurse_directory($path . "/" . $file, $base_url,
$path);
    }
    else
    {
        $url = "http://$HTTP_HOST/$path/$file";
        $url = str_replace("$DOCUMENT_ROOT", "", $url);
        echo "<li> <a href = \"$url\">$file</a></li>";
    }
    }
    }
    echo "</ul>";
}
recurse_directory();
?>
```

## 附录 H

### PHP 和 MySQL 资源

本附录提供了一些资源，这些资源对于提高你对 PHP 和 MySQL 的知识非常有用。

### PHP 资源

以下是一些关于 PHP 的优秀网站。

### PHP 网站

该网站位于 http://php.net， along with its many international mirrors，应是你的第二个家。从主页，你可以搜索手册或众多邮件列表之一。其中许多有用的资源包括：

- **PHP 注释手册** — (http://www.php.net/manual/) 在线手册非常出色；它包含用户评论，其中一些澄清了 PHP 中一些较难函数的用法。
- **下载** — (http://www.php.net/downloads) 在这里你可以找到各种发行版，以及可以下载并放在本地机器上的 HTML 手册。
- **每日快照** — (http://snaps.php.net) PHP 是一个活跃的开源项目，功能和错误修复不断添加到代码库中。在官方发布之前，你可以在这里获取最新代码。源代码每天更新。注意这最适合拥有专用开发机器的真正黑客。如果你只能安装一个版本，请获取最新的源代码。最新源代码的链接始终位于 http://www.php.net/ 的主页上。
- **错误数据库** — (http://bugs.php.net) 想知道某个函数是否存在问题？前往此网站搜索错误报告。这里也是你可以添加错误报告的地方。但在提交报告前，请务必确定你确实发现了错误。
- **常见问题:** (http://www.php.net/FAQ.php) 在向任何邮件列表发帖或开始编写应用程序之前，请阅读常见问题。
