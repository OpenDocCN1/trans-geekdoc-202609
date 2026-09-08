![](image_rsrc70M.jpg)

  

PHP MySQL

Cheat Sheet

( Cover all Basic PHP MySQL Syntaxes,

More Than 300 Examples )

Ray Yao

About This Book

This book covers all basic PHP syntaxes, almost each syntax entry lists a program example and result output. We can quickly reference the most helpful programming syntaxes, such as common command syntax, string function syntax, collection function syntax, class & object syntax……; all these syntaxes are very useful for programming.  
We can take this book as a basic syntax manual because its entries are arranged alphabetically so that we can easily reference the important syntax.

This book also includes the basic MySQL syntax related to the PHP.  
Nowadays or in the future, the PHP Syntax Book can provide great help for coding both in our study and our work.

Disclaimer

This book is intended as a basic syntax manual only; it cannot include all entries on this subject. Its purpose is as a supplement for a cheat sheet book, not as a whole PHP dictionary.

Copyright © 2015 by Ray Yao’s Team    

All Rights Reserved

Neither part of this book nor whole of this book may be reproduced or transmitted in any form or by any means electronic, photographic or mechanical, including photocopying, recording, or by any information storage or retrieval system, without prior written permission from the author. All rights reserved!

Ray Yao’s Team

Table of Contents

[Syntax Chart](#part0004.xhtml)

[<!--     --\> syntax:](#part0004.xhtml#a6HX)

[\_\_call() syntax:](#part0004.xhtml#a6HY)

[\_\_callstatic() syntax:](#part0004.xhtml#a6HZ)

[\_\_construct() syntax:](#part0004.xhtml#a6J0)

[\_\_destruct() syntax:](#part0004.xhtml#a6J1)

[$\_COOKIE\[ \] syntax:](#part0004.xhtml#a6J2)

[$\_ENV syntax:](#part0004.xhtml#a6J3)

[$\_FILE syntax:](#part0004.xhtml#a6J4)

[$\_GET\[ \] syntax:](#part0004.xhtml#a6J5)

[$\_POST\[ \] syntax:](#part0004.xhtml#a6J6)

[$\_REQUEST\[ \] syntax:](#part0004.xhtml#a6J7)

[$\_SERVER\[ \] syntax:](#part0004.xhtml#a6J8)

[$\_SERVER\["REQUEST\_METHOD"\] syntax:](#part0004.xhtml#a6J9)

[$\_SESSION\[ \] syntax:](#part0004.xhtml#a6JA)

[$\_SERVER\['PHP\_SELF'\] syntax:](#part0004.xhtml#a6JB)

[$GLOBALS syntax:](#part0004.xhtml#a6JC)

[$PHP\_SELF syntax:](#part0004.xhtml#a6JD)

[$this syntax:](#part0004.xhtml#a6JE)

[\=>  syntax:](#part0004.xhtml#a6JF)

[\== syntax:](#part0004.xhtml#a6JG)

[\=== syntax:](#part0004.xhtml#a6JH)

[++$var and $var++ syntax:](#part0004.xhtml#a6JJ)

[\--$var and $var-- syntax:](#part0004.xhtml#a6JK)

[? : operator syntax:](#part0004.xhtml#a6JM)

[<=> syntax:](#part0004.xhtml#a6JN)

[\_\_class\_\_ syntax:](#part0004.xhtml#a6JP)

[\_\_dir\_\_ syntax:](#part0004.xhtml#a6JR)

[\_\_file\_\_ syntax:](#part0004.xhtml#a6JS)

[\_\_function\_\_ syntax:](#part0004.xhtml#a6JT)

[\_\_line\_\_ syntax:](#part0004.xhtml#a6JU)

[\_\_method\_\_ syntax:](#part0004.xhtml#a6JV)

[\_\_namespace\_\_ syntax:](#part0004.xhtml#a6JW)

[\_\_trait\_\_ syntax:](#part0004.xhtml#a6JX)

[abs() syntax:](#part0004.xhtml#a6JY)

[abstract syntax:](#part0004.xhtml#a6JZ)

[addslashes() syntax:](#part0004.xhtml#a6K0)

[alter table syntax:](#part0004.xhtml#a6K1)

[alter table syntax:](#part0004.xhtml#a6K2)

[arithmetical operator syntax:](#part0004.xhtml#a6K3)

[array\_change\_key\_case() syntax:](#part0004.xhtml#a6K4)

[array\_chunk() syntax:](#part0004.xhtml#a6K5)

[array\_combine() syntax:](#part0004.xhtml#a6K6)

[array\_count\_values() syntax:](#part0004.xhtml#a6K7)

[array creating syntax:](#part0004.xhtml#a6K8)

[array creating syntax:](#part0004.xhtml#a6K9)

[array\_diff() syntax:](#part0004.xhtml#a6KA)

[array\_diff\_assoc() syntax:](#part0004.xhtml#a6KB)

[array\_diff\_key() syntax:](#part0004.xhtml#a6KC)

[array\_fill() syntax:](#part0004.xhtml#a6KD)

[array\_fill\_keys() syntax:](#part0004.xhtml#a6KE)

[array\_flip() syntax:](#part0004.xhtml#a6KF)

[array\_intersect() syntax:](#part0004.xhtml#a6KG)

[array\_intersect\_assoc() syntax:](#part0004.xhtml#a6KH)

[array\_intersect\_key() syntax:](#part0004.xhtml#a6KJ)

[array\_keys() syntax:](#part0004.xhtml#a6KK)

[array\_key\_exists() syntax:](#part0004.xhtml#a6KM)

[array\_merge() syntax:](#part0004.xhtml#a6KN)

[array\_multisort($arr) syntax:](#part0004.xhtml#a6KP)

[array\_pad() syntax:](#part0004.xhtml#a6KR)

[array\_pop() syntax:](#part0004.xhtml#a6KS)

[array\_product() syntax:](#part0004.xhtml#a6KT)

[array\_push() syntax:](#part0004.xhtml#a6KU)

[array\_rand() syntax:](#part0004.xhtml#a6KV)

[array\_reverse() syntax:](#part0004.xhtml#a6KW)

[array\_search() syntax:](#part0004.xhtml#a6KX)

[array\_shift() syntax:](#part0004.xhtml#a6KY)

[array size syntax:](#part0004.xhtml#a6KZ)

[array\_slice() syntax:](#part0004.xhtml#a6M0)

[array\_splice() syntax:](#part0004.xhtml#a6M1)

[array\_sum() syntax:](#part0004.xhtml#a6M2)

[array\_unique() syntax:](#part0004.xhtml#a6M3)

[array\_unshift() syntax:](#part0004.xhtml#a6M4)

[array\_values() syntax:](#part0004.xhtml#a6M5)

[arsort() syntax:](#part0004.xhtml#a6M6)

[asort() syntax:](#part0004.xhtml#a6M7)

[assignment syntax:](#part0004.xhtml#a6M8)

[between…and… syntax:](#part0004.xhtml#a6M9)

[break statement syntax:](#part0004.xhtml#a6MA)

[ceil() syntax:](#part0004.xhtml#a6MB)

[checkbox input syntax:](#part0004.xhtml#a6MC)

[chdir() syntax:](#part0004.xhtml#a6MD)

[checkdate() syntax:](#part0004.xhtml#a6ME)

[chmod() syntax:](#part0004.xhtml#a6MF)

[chop() syntax:](#part0004.xhtml#a6MG)

[chr() syntax:](#part0004.xhtml#a6MH)

[chunk\_split() syntax:](#part0004.xhtml#a6MJ)

[class definition syntax:](#part0004.xhtml#a6MK)

[Class::method() syntax:](#part0004.xhtml#a6MM)

[clearstatcache();](#part0004.xhtml#a6MN)

[close connection syntax:](#part0004.xhtml#a6MP)

[comment syntax:](#part0004.xhtml#a6MR)

[compact() syntax:](#part0004.xhtml#a6MS)

[conditional operator syntax:](#part0004.xhtml#a6MT)

[connect MySQL syntax:](#part0004.xhtml#a6MU)

[connect\_error() syntax:](#part0004.xhtml#a6MV)

[const syntax:](#part0004.xhtml#a6MW)

[constant() syntax:](#part0004.xhtml#a6MX)

[constructor syntax:](#part0004.xhtml#a6MY)

[continue statement syntax:](#part0004.xhtml#a6MZ)

[copy() syntax:](#part0004.xhtml#a6N0)

[count() syntax:](#part0004.xhtml#a6N1)

[count\_chars() syntax:](#part0004.xhtml#a6N2)

[create database syntax:](#part0004.xhtml#a6N3)

[create database syntax:](#part0004.xhtml#a6N4)

[create table syntax:](#part0004.xhtml#a6N5)

[create table syntax:](#part0004.xhtml#a6N6)

[crypt() syntax:](#part0004.xhtml#a6N7)

[ctype\_alnum() syntax:](#part0004.xhtml#a6N8)

[ctype\_alpha() syntax:](#part0004.xhtml#a6N9)

[current() syntax:](#part0004.xhtml#a6NA)

[date() syntax:](#part0004.xhtml#a6NB)

[dechex() syntax:](#part0004.xhtml#a6NC)

[define() syntax:](#part0004.xhtml#a6ND)

[delete record syntax:](#part0004.xhtml#a6NE)

[delete record syntax:](#part0004.xhtml#a6NF)

[describe table syntax:](#part0004.xhtml#a6NG)

[die() syntax:](#part0004.xhtml#a6NH)

[do-while loop syntax:](#part0004.xhtml#a6NJ)

[drop a field syntax:](#part0004.xhtml#a6NK)

[each() syntax:](#part0004.xhtml#a6NM)

[echo syntax:](#part0004.xhtml#a6NN)

[error\_log() syntax:](#part0004.xhtml#a6NP)

[empty() syntax:](#part0004.xhtml#a6NR)

[encapsulation syntax:](#part0004.xhtml#a6NS)

[enctype syntax:](#part0004.xhtml#a6NT)

[end() syntax:](#part0004.xhtml#a6NU)

[explain table syntax:](#part0004.xhtml#a6NV)

[exit() syntax:](#part0004.xhtml#a6NW)

[explode() syntax:](#part0004.xhtml#a6NX)

[extends syntax:](#part0004.xhtml#a6NY)

[eval() syntax:](#part0004.xhtml#a6NZ)

[exec() syntax:](#part0004.xhtml#a6P0)

[extract() syntax:](#part0004.xhtml#a6P1)

[fclose() syntax:](#part0004.xhtml#a6P2)

[feof() syntax:](#part0004.xhtml#a6P3)

[fgetc() syntax:](#part0004.xhtml#a6P4)

[fgetcvs() syntax:](#part0004.xhtml#a6P5)

[fgets() syntax:](#part0004.xhtml#a6P6)

[file() syntax:](#part0004.xhtml#a6P7)

[fileatime() syntax:](#part0004.xhtml#a6P8)

[filemtime() syntax:](#part0004.xhtml#a6P9)

[file uploading syntax:](#part0004.xhtml#a6PA)

[file\_exists() syntax:](#part0004.xhtml#a6PB)

[filesize() syntax:](#part0004.xhtml#a6PC)

[file\_get\_contents() syntax:](#part0004.xhtml#a6PD)

[file\_put\_contents() syntax:](#part0004.xhtml#a6PE)

[filter\_callback syntax:](#part0004.xhtml#a6PF)

[filter\_has\_var() syntax:](#part0004.xhtml#a6PG)

[filter\_input syntax:](#part0004.xhtml#a6PH)

[filter\_input\_array() syntax:](#part0004.xhtml#a6PJ)

[filter\_var() syntax:](#part0004.xhtml#a6PK)

[filter\_var\_array() syntax:](#part0004.xhtml#a6PM)

[final syntax:](#part0004.xhtml#a6PN)

[floatval() syntax:](#part0004.xhtml#a6PP)

[floor() syntax:](#part0004.xhtml#a6PR)

[flush() syntax:](#part0004.xhtml#a6PS)

[fopen() syntax:](#part0004.xhtml#a6PT)

[for loop syntax:](#part0004.xhtml#a6PU)

[foreach() syntax:](#part0004.xhtml#a6PV)

[fprintf() syntax:](#part0004.xhtml#a6PW)

[fputs() syntax:](#part0004.xhtml#a6PX)

[fread() syntax:](#part0004.xhtml#a6PY)

[fscanf() syntax:](#part0004.xhtml#a6PZ)

[ftruncate() syntax;](#part0004.xhtml#a6R0)

[function syntax:](#part0004.xhtml#a6R1)

[function with argument syntax:](#part0004.xhtml#a6R2)

[fwrite() syntax:](#part0004.xhtml#a6R3)

[getcwd() syntax:](#part0004.xhtml#a6R4)

[getdate() syntax:](#part0004.xhtml#a6R5)

[get\_resource\_type() syntax:](#part0004.xhtml#a6R6)

[getenv() syntax:](#part0004.xhtml#a6R7)

[getFile() syntax:](#part0004.xhtml#a6R8)

[getLine() syntax:](#part0004.xhtml#a6R9)

[getMessage() syntax:](#part0004.xhtml#a6RA)

[global variable syntax:](#part0004.xhtml#a6RB)

[gmdate() syntax:](#part0004.xhtml#a6RC)

[gmmktime() syntax:](#part0004.xhtml#a6RD)

[header syntax;](#part0004.xhtml#a6RE)

[heredoc syntax:](#part0004.xhtml#a6RF)

[htmlentities() syntax:](#part0004.xhtml#a6RG)

[html\_entity\_decode() syntax:](#part0004.xhtml#a6RH)

[htmlspecialchars() syntax:](#part0004.xhtml#a6RJ)

[htmlspecialchars\_decode() syntax:](#part0004.xhtml#a6RK)

[http\_build\_query() syntax:](#part0004.xhtml#a6RM)

[iconv() syntax:](#part0004.xhtml#a6RN)

[if statement syntax:](#part0004.xhtml#a6RP)

[if-else Statement syntax:](#part0004.xhtml#a6RR)

[if…elseif…else syntax:](#part0004.xhtml#a6RS)

[implode() syntax:](#part0004.xhtml#a6RT)

[in\_array() syntax:](#part0004.xhtml#a6RU)

[include() syntax:](#part0004.xhtml#a6RV)

[include\_once() syntax:](#part0004.xhtml#a6RW)

[insert into table syntax:](#part0004.xhtml#a6RX)

[insert into table syntax:](#part0004.xhtml#a6RY)

[insert into table syntax:](#part0004.xhtml#a6RZ)

[intdiv() syntax:](#part0004.xhtml#a6S0)

[interface syntax:](#part0004.xhtml#a6S1)

[is\_dir() syntax:](#part0004.xhtml#a6S2)

[is\_file() syntax:](#part0004.xhtml#a6S3)

[is\_int() syntax:](#part0004.xhtml#a6S4)

[is\_integer() syntax:](#part0004.xhtml#a6S5)

[is\_null() syntax:](#part0004.xhtml#a6S6)

[is\_numeric() syntax:](#part0004.xhtml#a6S7)

[is\_readable() syntax:](#part0004.xhtml#a6S8)

[is\_string() syntax:](#part0004.xhtml#a6S9)

[isset() syntax:](#part0004.xhtml#a6SA)

[is\_executable() syntax:](#part0004.xhtml#a6SB)

[is\_writable() syntax:](#part0004.xhtml#a6SC)

[is\_writeable() syntax:](#part0004.xhtml#a6SD)

[json\_decode() syntax:](#part0004.xhtml#a6SE)

[json\_encode() syntax:](#part0004.xhtml#a6SF)

[key() syntax:](#part0004.xhtml#a6SG)

[krsort() syntax:](#part0004.xhtml#a6SH)

[ksort() syntax:](#part0004.xhtml#a6SJ)

[less / more than syntax:](#part0004.xhtml#a6SK)

[limit records syntax:](#part0004.xhtml#a6SM)

[list() syntax:](#part0004.xhtml#a6SN)

[local variable syntax:](#part0004.xhtml#a6SP)

[log() syntax:](#part0004.xhtml#a6SR)

[ltrim() syntax:](#part0004.xhtml#a6SS)

[mail() syntax:](#part0004.xhtml#a6ST)

[max() syntax:](#part0004.xhtml#a6SU)

[md5() syntax:](#part0004.xhtml#a6SV)

[md5\_file() syntax:](#part0004.xhtml#a6SW)

[microtime() syntax:](#part0004.xhtml#a6SX)

[min() syntax:](#part0004.xhtml#a6SY)

[mkdir() syntax:](#part0004.xhtml#a6SZ)

[mktime() syntax:](#part0004.xhtml#a6T0)

[move\_uploaded\_file() syntax:](#part0004.xhtml#a6T1)

[mt\_rand() syntax:](#part0004.xhtml#a6T2)

[mysqli\_affected\_rows() syntax:](#part0004.xhtml#a6T3)

[mysqli\_close( ) syntax:](#part0004.xhtml#a6T4)

[mysqli\_connect() syntax:](#part0004.xhtml#a6T5)

[mysqli\_connect\_error() syntax:](#part0004.xhtml#a6T6)

[mysqli\_data\_seek() syntax:](#part0004.xhtml#a6T7)

[mysqli\_error() syntax:](#part0004.xhtml#a6T8)

[mysqli\_fetch\_array() syntax:](#part0004.xhtml#a6T9)

[mysqli\_fetch\_assoc() syntax:](#part0004.xhtml#a6TA)

[mysqli\_fetch\_row() syntax:](#part0004.xhtml#a6TB)

[mysqli\_free\_result() syntax:](#part0004.xhtml#a6TC)

[mysqli\_get\_server\_info() syntax:](#part0004.xhtml#a6TD)

[mysqli\_num\_rows() syntax:](#part0004.xhtml#a6TE)

[mysqli\_query() syntax:](#part0004.xhtml#a6TF)

[mysqli\_real\_escape\_string() syntax:](#part0004.xhtml#a6TG)

[mysqli\_result() syntax:](#part0004.xhtml#a6TH)

[mysqli\_select\_db() syntax:](#part0004.xhtml#a6TJ)

[namespace syntax:](#part0004.xhtml#a6TK)

[natcasesort() syntax:](#part0004.xhtml#a6TM)

[natsort() syntax:](#part0004.xhtml#a6TN)

[next() syntax:](#part0004.xhtml#a6TP)

[nl2br() syntax:](#part0004.xhtml#a6TR)

[not equal syntax:](#part0004.xhtml#a6TS)

[null value syntax:](#part0004.xhtml#a6TT)

[number\_format() syntax:](#part0004.xhtml#a6TU)

[ob\_clean() syntax:](#part0004.xhtml#a6TV)

[ob\_end\_clean() syntax:](#part0004.xhtml#a6TW)

[ob\_end\_flush() syntax:](#part0004.xhtml#a6TX)

[ob\_flush() syntax:](#part0004.xhtml#a6TY)

[ob\_get\_clean() syntax:](#part0004.xhtml#a6TZ)

[ob\_get\_flush() syntax:](#part0004.xhtml#a6U0)

[ob\_get\_contents() syntax:](#part0004.xhtml#a6U1)

[ob\_get\_length()](#part0004.xhtml#a6U2)

[ob\_get\_level() syntax:](#part0004.xhtml#a6U3)

[ob\_start() syntax:](#part0004.xhtml#a6U4)

[object syntax:](#part0004.xhtml#a6U5)

[order by syntax:](#part0004.xhtml#a6U6)

[overloading syntax:](#part0004.xhtml#a6U7)

[override syntax:](#part0004.xhtml#a6U8)

[parent::\_\_construct() syntax:](#part0004.xhtml#a6U9)

[parse\_str() syntax:](#part0004.xhtml#a6UA)

[PHP\_EOL syntax:](#part0004.xhtml#a6UB)

[phpinfo() syntax:](#part0004.xhtml#a6UC)

[pi() syntax:](#part0004.xhtml#a6UD)

[polymorphism syntax:](#part0004.xhtml#a6UE)

[pow() syntax:](#part0004.xhtml#a6UF)

[preg\_match() syntax:](#part0004.xhtml#a6UG)

[preg\_match\_all() syntax:](#part0004.xhtml#a6UH)

[preg\_replace() syntax:](#part0004.xhtml#a6UJ)

[preg\_split() syntax:](#part0004.xhtml#a6UK)

[prepare() syntax:](#part0004.xhtml#a6UM)

[prev() syntax:](#part0004.xhtml#a6UN)

[print syntax:](#part0004.xhtml#a6UP)

[printf() syntax:](#part0004.xhtml#a6UR)

[print\_r() syntax:](#part0004.xhtml#a6US)

[private syntax:](#part0004.xhtml#a6UT)

[protected syntax:](#part0004.xhtml#a6UU)

[public syntax:](#part0004.xhtml#a6UV)

[putenv() syntax:](#part0004.xhtml#a6UW)

[query() syntax:](#part0004.xhtml#a6UX)

[radio button syntax:](#part0004.xhtml#a6UY)

[rand() syntax:](#part0004.xhtml#a6UZ)

[readfile() syntax:](#part0004.xhtml#a6V0)

[remove database syntax:](#part0004.xhtml#a6V1)

[remove table syntax:](#part0004.xhtml#a6V2)

[rename() syntax:](#part0004.xhtml#a6V3)

[require() syntax:](#part0004.xhtml#a6V4)

[require\_once() syntax:](#part0004.xhtml#a6V5)

[reset form syntax:](#part0004.xhtml#a6V6)

[reset() syntax:](#part0004.xhtml#a6V7)

[return syntax:](#part0004.xhtml#a6V8)

[rmdir() syntax:](#part0004.xhtml#a6V9)

[round() syntax:](#part0004.xhtml#a6VA)

[rsort() syntax:](#part0004.xhtml#a6VB)

[rtrim() syntax:](#part0004.xhtml#a6VC)

[scandir() syntax:](#part0004.xhtml#a6VD)

[select data syntax:](#part0004.xhtml#a6VE)

[select data syntax:](#part0004.xhtml#a6VF)

[select to show table syntax:](#part0004.xhtml#a6VG)

[select option syntax:](#part0004.xhtml#a6VH)

[serialize() syntax:](#part0004.xhtml#a6VJ)

[session\_destroy() syntax:](#part0004.xhtml#a6VK)

[session\_id()syntax:](#part0004.xhtml#a6VM)

[session\_name() syntax:](#part0004.xhtml#a6VN)

[session\_regenerate\_id() syntax:](#part0004.xhtml#a6VP)

[session\_start() syntax:](#part0004.xhtml#a6VR)

[session\_status() syntax:](#part0004.xhtml#a6VS)

[session\_unset() syntax:](#part0004.xhtml#a6VT)

[session\_write\_close() syntax:](#part0004.xhtml#a6VU)

[set\_error\_handler() syntax:](#part0004.xhtml#a6VV)

[set\_exception\_handler() syntax:](#part0004.xhtml#a6VW)

[setcookie() syntax:](#part0004.xhtml#a6VX)

[sha1() syntax:](#part0004.xhtml#a6VY)

[sha1\_file() syntax:](#part0004.xhtml#a6VZ)

[show databases syntax:](#part0004.xhtml#a6W0)

[show specified field syntax:](#part0004.xhtml#a6W1)

[show specified record syntax:](#part0004.xhtml#a6W2)

[show tables syntax:](#part0004.xhtml#a6W3)

[shuffle() syntax:](#part0004.xhtml#a6W4)

[simplexml\_load\_file() syntax:](#part0004.xhtml#a6W5)

[simplexml\_load\_string() syntax:](#part0004.xhtml#a6W6)

[sleep() syntax:](#part0004.xhtml#a6W7)

[sort() syntax:](#part0004.xhtml#a6W8)

[sort table data syntax:](#part0004.xhtml#a6W9)

[sprintf() syntax:](#part0004.xhtml#a6WA)

[sqrt() syntax:](#part0004.xhtml#a6WB)

[sscanf() syntax:](#part0004.xhtml#a6WC)

[static syntax:](#part0004.xhtml#a6WD)

[static member syntax:](#part0004.xhtml#a6WE)

[string syntax:](#part0004.xhtml#a6WF)

[string connecting syntax:](#part0004.xhtml#a6WG)

[stripos() syntax:](#part0004.xhtml#a6WH)

[stripslashes() syntax:](#part0004.xhtml#a6WJ)

[stristr() syntax:](#part0004.xhtml#a6WK)

[strip\_tags() syntax:](#part0004.xhtml#a6WM)

[str\_ireplace() syntax:](#part0004.xhtml#a6WN)

[strlen( ) syntax:](#part0004.xhtml#a6WP)

[str\_pad() syntax:](#part0004.xhtml#a6WR)

[strpbrk() syntax:](#part0004.xhtml#a6WS)

[strpos() syntax:](#part0004.xhtml#a6WT)

[str\_repeat() syntax:](#part0004.xhtml#a6WU)

[strrev() syntax:](#part0004.xhtml#a6WV)

[strripos() syntax:](#part0004.xhtml#a6WW)

[strrpos() syntax:](#part0004.xhtml#a6WX)

[strstr() syntax:](#part0004.xhtml#a6WY)

[strtolower( ) syntax:](#part0004.xhtml#a6WZ)

[strtotime() syntax:](#part0004.xhtml#a6X0)

[strtoupper() syntax:](#part0004.xhtml#a6X1)

[str\_replace() syntax:](#part0004.xhtml#a6X2)

[str\_shuffle() syntax:](#part0004.xhtml#a6X3)

[str\_split() syntax:](#part0004.xhtml#a6X4)

[str\_word\_count() syntax:](#part0004.xhtml#a6X5)

[strtr() syntax:](#part0004.xhtml#a6X6)

[submit form syntax:](#part0004.xhtml#a6X7)

[substr() syntax:](#part0004.xhtml#a6X8)

[substr\_count() syntax:](#part0004.xhtml#a6X9)

[substr\_replace() syntax:](#part0004.xhtml#a6XA)

[switch syntax:](#part0004.xhtml#a6XB)

[text input syntax:](#part0004.xhtml#a6XC)

[textarea input syntax:](#part0004.xhtml#a6XD)

[time() syntax:](#part0004.xhtml#a6XE)

[trait syntax:](#part0004.xhtml#a6XF)

[trigger\_error() syntax:](#part0004.xhtml#a6XG)

[trim() syntax:](#part0004.xhtml#a6XH)

[try / throw / catch() syntax:](#part0004.xhtml#a6XJ)

[ucfirst() syntax:](#part0004.xhtml#a6XK)

[ucwords() syntax:](#part0004.xhtml#a6XM)

[uniqid() syntax:](#part0004.xhtml#a6XN)

[unlink() syntax:](#part0004.xhtml#a6XP)

[unserialize() syntax:](#part0004.xhtml#a6XR)

[unset() syntax:](#part0004.xhtml#a6XS)

[update table syntax:](#part0004.xhtml#a6XT)

[update table syntax:](#part0004.xhtml#a6XU)

[urldecode() syntax:](#part0004.xhtml#a6XV)

[urlencode() syntax:](#part0004.xhtml#a6XW)

[Use Database syntax:](#part0004.xhtml#a6XX)

[usleep() syntax:](#part0004.xhtml#a6XY)

[variable syntax:](#part0004.xhtml#a6XZ)

[var\_dump() syntax:](#part0004.xhtml#a6Y0)

[where condition syntax:](#part0004.xhtml#a6Y1)

[while Loop syntax:](#part0004.xhtml#a6Y2)

[wordwrap() syntax:](#part0004.xhtml#a6Y3)

[xml dom parser syntax:](#part0004.xhtml#a6Y4)

[Appendix](#part0005.xhtml)

[PHP Reserved Words Chart](#part0005.xhtml#a6Y6)

[PHP Escaping Characters Chart](#part0005.xhtml#a6Y7)

[PHP Predefined Characters Chart](#part0005.xhtml#a6Y8)

[PHP File Opening Mode Chart](#part0006.xhtml)

[PHP Email Functions Chart](#part0006.xhtml#a6YA)

[PHP Filter Functions Chart](#part0006.xhtml#a6YB)

[PHP File Permission Chart](#part0007.xhtml)

[PHP String Format Chart](#part0007.xhtml#a6YD)

[PHP Data & Time Format Chart](#part0008.xhtml)

[PHP Data Type Chart](#part0008.xhtml#a6YF)

[mysqli\_xxx\_xxx (  ) Chart](#part0009.xhtml)

[MySQL Database Commands Chart](#part0010.xhtml)

[MySQL Table Commands Chart](#part0010.xhtml#a6YJ)

[MySQL Operation Commands Chart](#part0010.xhtml#a6YK)

[MySQL Data Type Chart](#part0011.xhtml)

[MySQL Field Modifier Chart](#part0011.xhtml#a6YN)

[MySQL System Function Chart](#part0011.xhtml#a6YP)

[MySQL Numeric Function Chart](#part0012.xhtml)

[MySQL Datetime Function Chart](#part0012.xhtml#a6YS)

[MySQL Statement Chart](#part0013.xhtml)

[Cheat Sheet by Ray Yao](#part0013.xhtml#a6YU)

# Syntax Chart

\-------------------------------------------------------------------------------

<!--     --\> syntax:

<!-\- html comment \-->

// The <!\-\-     \-\-\> is a comment symbol of html

// PHP or HTML compiler always ignores the html comment.

e.g.

<html>

Hello World!   <!\-\- show Hello World! \-\->

</html>

// Output:   Hello World!

\-------------------------------------------------------------------------------

\_\_call() syntax:

function \_\_call($funName, $arg){…}

// \_\_call() is invoked when an inexistent function is called in an object context.

// $funName is the function name, $arg is an array parameter.

e.g.

<?php

class MyClass{

public function \_\_call($funName, $arg){  

echo "Calling '$funName' ". implode(' ', $arg);

}}

$obj = new MyClass;

$obj \-\> myFun( 'that is inexistent' );   // myFun isn't existing in fact

?>

// Output:   Calling 'myFun' that is inexistent

\-------------------------------------------------------------------------------

\_\_callstatic() syntax:

function \_\_callstatic($funName, $arg){…}

// \_\_callstatic() is invoked when an inexistent function is called in a static context.

// $funName is the function name, $arg is an array parameter

e.g.

<?php

class MyClass{

public static function \_\_callStatic($funName, $arg){

echo "Calling '$funName' ". implode(' ', $arg);

}}

$obj = new MyClass;

MyClass::myFun( 'that is inexistent' );   // myFun isn't existing in fact

?>

// Output:   Calling 'myFun' that is inexistent

\-------------------------------------------------------------------------------

\_\_construct() syntax:

function \_\_construct($arg);    

// Constructor is used to initialize the class's variables

e.g.

<?php

class Flower{    // define a class "Flower"

var $c;

function \_\_construct($arg) {  // constructor

$this\-\>c= $arg;   // initialize the variable "c"

}}     // $this represents the current object $obj

$obj= new Flower( 'beautiful' );     // create an object "$obj"

echo $obj\-\>c;

?>

// Output:  beautiful

\-------------------------------------------------------------------------------

\_\_destruct() syntax:

function \_\_destruct{}

// Destructor release the constructor resources. The destructor will be called when the object is destroyed or the program is stopped or exited.

e.g.

<?php

class Flower{

var $c;

function \_\_construct($arg) {    // define a constructor

$this\-\>c= $arg;   echo $this\-\>c;

}

function \_\_destruct( ) {   // define a destructor

echo " Destructor runs… ";

}}

$obj= new Flower( ' Constructor runs… ' );

?>

// Output:     Constructor runs…  Destructor runs…

\-------------------------------------------------------------------------------

$\_COOKIE\[ \] syntax:

setcookie ( "name",  "value" );  // set cookie name and value

$\_COOKIE\["name"\];  // get cookie value by cookie name

e.g.

<!\-- aFile.php -->

<?php   // in aFile.php

setcookie("color", "blue");   // set a cookie

// cookie name is "color", cookie value is "blue"

header("location: bFile.php");      // redirect to bFile.php

?>

<!\-\-save this file with the name "aFile.php" in the working folder\-\->

<!\-\- bFile.php -->

<?php   // in bFile.php

$mycolor = $\_COOKIE\["color"\];  // get the cookie from aFile.php

// get the cookie whose name is "color"

echo  $mycolor;    // show the color's value

?>

<!\-\-save the file with the name "bFile.php" in the working folder\-\->

<!\-\-please run the aFile.php\-\-\> 

// Output:     blue

\-------------------------------------------------------------------------------

$\_ENV syntax:

$\_ENV\["VARIABLE"\]

// Contain the information about the environment variables.

e.g.

$\_ENV\["USER"\] = "Ray Yao";

echo 'The username is: ' .$\_ENV\["USER"\];

// Output:  

The username: Ray Yao

\-------------------------------------------------------------------------------

$\_FILE syntax:

$\_FILES\['file'\]\['name'\]  // The name of the file to be uploaded.

$\_FILES\['file'\]\['type'\]  // The mime type of the file.

$\_FILES\['file'\]\['size'\]  // The byte size of the uploaded file.

$\_FILES\['file'\]\['tmp\_name'\]  // The temporary file name in server.

$\_FILES\['file'\]\['error'\]  // The error information of the uploaded file.

e.g.   // Assume that we upload a file named "myFile.txt"

<form action="" method="post" enctype="multipart/form-data">

<input type="file" name="file">

<input type ="submit" value="Submit">

</form>

<?php

echo "File Name: " . $\_FILES\['file'\]\['name'\]."<br>";

echo "File Type : " . $\_FILES\['file'\]\['type'\]."<br>";

echo "File Size : " . $\_FILES\['file'\]\['size'\]."<br>";

echo "Temp Name: " . $\_FILES\['file'\]\['tmp\_name'\]."<br>";

echo "Error Info: " . $\_FILES\['file'\]\['error'\]. "<br>";

?>

// Output:  

![](image_rsrc70N.jpg)

File Name: myFile.txt  
File Type : text/plain  
File Size : 279  
Temp Name: C:\\Windows\\Temp\\php5167.tmp  
Error Info: 0

\-------------------------------------------------------------------------------

$\_GET\[ \] syntax:

$myData=$\_GET\[ data \];

// Get data from the HTML form and assigns its value to $myData.

e.g.

<html>

<form action=" "  method="get">

<input type="text"  name="data">

<!\-\- the inputted value will be stored to the "data" \-\->

<!\-\-"data" will be passed to the PHP file for processing. -\->

</form>

<?php    // Assume that we input "Hello, World!" in the text box

$myData = $\_GET\[ data \];  

// $\_GET\[ data \] gets the "data" value from the html form

echo ("You have inputted: ".$myData);     // show data value

?>

</html>

// Output

| Hello, World! |
| --- |

You have inputted: Hello, World!

\-------------------------------------------------------------------------------

$\_POST\[ \] syntax:

$myData=$\_POST\[ data \];

// Post data from the HTML form and assigns its value to $myData.

e.g.

<html>

<form action=" "  method="post">

<input type="text"  name="data">

<!\-\- the inputted value will be stored to the "data" \-\->

<!\-\-"data" will be passed to the PHP file for processing. -\->

</form>

<?php    // Assume that we input "Hello, World!" in the text box

$myData = $\_POST\[ data \];  

// $\_POST\[ data \] posts the "data" value from the html form

echo ("You have inputted: ".$myData);     // show data value

?>

</html>

// Output

| Hello, World! |
| --- |

You have inputted: Hello, World!

\-------------------------------------------------------------------------------

$\_REQUEST\[ \] syntax:

$myData=$\_REQUEST\[data\];

// Obtain data from the HTML form and assigns its value to $myData.

e.g.

<html>

<form action=" "  method="request">

<input type="text"  name="data">

<!\-\- the inputted value will be stored to the "data" \-\->

<!\-\-"data" will be passed to the PHP file for processing. -\->

</form>

<?php    // Assume that we input "Hello, World!" in the text box

$myData = $\_REQUEST\[data\];  

// $\_REQUEST\[data\] gets the "data" value from the html form

echo ("You have inputted: ".$myData);     // show data value

?>

</html>

// Output

| Hello, World! |
| --- |

You have inputted: Hello, World!

\-------------------------------------------------------------------------------

$\_SERVER\[ \] syntax:

$\_SERVER\["HTTP\_USER\_AGENT"\];

// Return the information about the browser of a visitor

e.g.

$browser = $\_SERVER\["HTTP\_USER\_AGENT"\];

echo "$browser";   

// Output:   Mozilla/4.0 (compatible; MSIE 8.0)…

\-------------------------------------------------------------------------------

$\_SERVER\["REQUEST\_METHOD"\] syntax:

$\_SERVER\["REQUEST\_METHOD"\]

// Returns the request method used to access the page

e.g.

<?php

$name = "";

if ($\_SERVER\["REQUEST\_METHOD"\]=="POST"){

// check if the form can be submitted

$name = $\_POST\["name"\];

}

?>

<form method="post" action="">

Name: <input type="text" name="name">

</form>

<?php echo $name; ?>

// Output:  

![](image_rsrc70P.jpg)

Ray Yao

\-------------------------------------------------------------------------------

$\_SESSION\[ \] syntax:

$\_SESSION\["name"\] = value;     // set session name & value

$\_SESSION\["name"\];      // get session value by name

e.g.

1.      <!\-- aFile.php -\->

<?php  session\_start( );   

$\_SESSION \["color"\] = "green";    // set color as green

header("location: bFile.php");

?>     <!\-- save this file as aFile.php -\->

2.      <!\-\- bFile.php -\->

<?php  session\_start( );   

$carColor = $\_SESSION \["color"\];   // get the value of color

echo $carColor;

?>        <!\-\- save this file as bFile.php -\->

<!\-\- please run the aFile.php \-\->

// Output:   green

\-------------------------------------------------------------------------------

$\_SERVER\['PHP\_SELF'\] syntax:

action="<?php echo($\_SERVER\['PHP\_SELF'\]);?>"

// Send form data to the current page instead of another page.

e.g.

<html>

<form action="<?php echo($\_SERVER\['PHP\_SELF'\]);?>" method="post">

Name: <input type="text" name="myName">

<input type="submit" value="Submit">

</form>

<?php echo $\_POST\["myName"\]; ?><br>

</html>

// Output:

![](image_rsrc70R.jpg)

Ray Yao

\-------------------------------------------------------------------------------

$GLOBALS syntax:

$GLOBALS\['variable'\]

// $GLOBALS is a PHP super global variable that is accessible in all scopes of a PHP program

e.g.

<?php

$a = 100; $b = 200;

function fun() {

$GLOBALS\['c'\] = $GLOBALS\['a'\] + $GLOBALS\['b'\];

}

fun();

echo $c;

?>

// Output:   300

\-------------------------------------------------------------------------------

$PHP\_SELF syntax:

action="<?php echo($PHP\_SELF);?>"

// Send form data to the current page instead of another page.

e.g.

<html>

<form action="<?php echo($PHP\_SELF);?>" method="post">

Name: <input type="text" name="myName">

<input type="submit" value="Submit">

</form>

<?php echo $\_POST\["myName"\]; ?><br>

</html>

// Output:

![](image_rsrc70R.jpg)

Ray Yao

\-------------------------------------------------------------------------------

$this syntax:

$this \-\> property;

//"$this \-\> property;" is used to access the property in the current class.

// $this represents the current object.

// Note:  the property has no $ symbol in the "$this \-\> property"

e.g.

<?php

class ThisDemo{        // define a class "ThisDemo"

var $t = "\\$this syntax example";

function myFun() {

echo $this\->t;     // $this represents $obj

}}

$obj= new ThisDemo();    // create an object

$obj\->myFun();   // $obj references the myFun(){ }

?>

// Output:   $this syntax example

\-------------------------------------------------------------------------------

\=>  syntax:

array( key1=>value1, key2=>value2, kay3=>value3…);

// "=>" symbol is used to connect key and value.

// key and index is the same meaning in Array.

e.g.

<?php

$book=array( "A"=>"JSP", "B"=>"ASP", "C"=>"PHP");    

// "A, B, C" are keys, "JSP, ASP, PHP" are values.

echo $book\[ "C" \];   // show the element value in the key "C"

?>

// Output:  PHP

\-------------------------------------------------------------------------------

\== syntax:

value1 == value2

// Compare two values, but not compare the type of two values

e.g.

if(9 == "9"){ echo 'equal'; }

else{ echo 'not equal'; }

// Output:   equal

\-------------------------------------------------------------------------------

\=== syntax:

value1 === value2

// Compare two values, and compare the type of two values

e.g.

if(9 === "9"){echo 'equal';}

else{ echo 'not equal';}

// Output:   not equal

\-------------------------------------------------------------------------------

++$var and $var++ syntax:

++$var   // $var plus 1, and return $var

$var++   // returns $var, and then $var plus 1

e.g.

$x=100; echo ++$x;    // Output 101

$y=100; echo $y++;    // Output 100

\-------------------------------------------------------------------------------

\--$var and $var-- syntax:

\--$var   // $var minus 1, and return $var

$var--   // returns $var, and then $var minus 1

e.g.

$x=100; echo \--$x;    // Output 99

$y=100; echo $y--;    // Output 100

\-------------------------------------------------------------------------------

? : operator syntax:

(test-expression) ? (if-true-do-this) : (if-false-do-this);

// Conditional operator checks if the test-expression is true or false, then, according to true or false to execute the specified block.

e.g.

$a = 100; $b = 200;

$result = ($a<$b) ? "apple " : "banana ";

// (check if $a<$b) ? (if-true-do-this) : (if-false-do-this);

echo ("$result<br>");

// Output:   apple

\-------------------------------------------------------------------------------

<=> syntax:

$c = $a <=> $b;

// If $a > $b, then the value of $c is 1.

// If $a == $b, the value of $c is 0.

// If $a < $b, then the value of $c is -1.

e.g.

echo 10 <=> 10;    // 0

echo 3.14 <=> 3.10;    // 1

echo "ant" <=> "bee";     // -1

\-------------------------------------------------------------------------------

\_\_class\_\_ syntax:

\_\_class\_\_

// Return the current class name.

e.g.

<?php

class MyClass {

function myFun() {

echo 'The current class name is '  . \_\_class\_\_ ;      

}}

$obj = new MyClass();

$obj\-\>myFun();

?>

// Output:  The current class name is MyClass

\-------------------------------------------------------------------------------

\_\_dir\_\_ syntax:

\_\_dir\_\_

// Return the directory of the current file

e.g.

echo 'The directory of the current file is '  . \_\_dir\_\_ ;

// Output:   The directory of the current file is C:\\AppServ\\www

\-------------------------------------------------------------------------------

\_\_file\_\_ syntax:

\_\_file\_\_

// Return the current file path and file name

e.g.

echo 'The current file path and file name are '  . \_\_file\_\_ ;

// Output:

The current file path and file name are C:\\AppServ\\www\\myFile.php

\------------------------------------------------------------------------------

\_\_function\_\_ syntax:

\_\_function\_\_

// Return the current function name.

e.g.

<?php

function myFun() {

echo  'The current function name is ' . \_\_function\_\_ ;

}

myFun();

?>

// Output:   The current function name is myFun

\-------------------------------------------------------------------------------

\_\_line\_\_ syntax:

\_\_line\_\_

// Return the current line number in the file

e.g.

echo ' The current line number is '  . \_\_line\_\_ ;

// Output:   The current line number is 2.

\-------------------------------------------------------------------------------

\_\_method\_\_ syntax:

\_\_method\_\_

// Return the method name of a class

e.g.

function myFun() {

echo  'The function name is ' . \_\_method\_\_ ;

}

myFun();

// Output:   The function name is myFun

\-------------------------------------------------------------------------------

\_\_namespace\_\_ syntax:

\_\_namespace\_\_

// Return the name of namespace.

e.g.

namespace MyNamespace;

echo 'The namespace is ', \_\_namespace\_\_;     

// Output:   The namespace is MyNamespace.

\-------------------------------------------------------------------------------

\_\_trait\_\_ syntax:

\_\_trait\_\_

// Return a trait name.

// Trait is used to define a method that can be used in multiple classes.

// Trait enables programmers to reuse a method in different classes.

e.g.

<?php

trait myTrait{

function myFun(){

echo  'The trait name is ' . \_\_trait\_\_ ;  // return the trait name

}}

class MyClass{

use myTrait;

}

$obj = new MyClass;

$obj\-\>myFun();

?>

// Output:   The trait name is myTrait

\-------------------------------------------------------------------------------

abs() syntax:

abs(number)

// Return the absolute value of different numbers

e.g.

echo(abs(-12.345));

// Output:   12.345

\-------------------------------------------------------------------------------

abstract syntax:

abstract BaseClass{abstract method();}

class DerivedClass implements BaseClass{method(){}}

// Abstracts class and method are defined by the abstract keyword.

// An abstract class contains at least one abstract method. Abstract method has no body, but need its derived class to complete the task.

// The method of the derived class can override the abstract method of the abstract base class.

e.g.

<?php

abstract class Base {     // define a abstract class

abstract function show();     // define a abstract method

}

class Derived extends Base {

function show() {

echo "Implement the abstract function";

}}

$obj = new Derived;

$obj\-\>show();

?>

// Output:   Implement the abstract function

\-------------------------------------------------------------------------------

addslashes() syntax:

addslashes(" single quote or double quote ")

// Add a backslash in front of each single quote double quote.

e.g.

$str = addslashes("This is a 'good' food!");

echo($str);

// Output:   This is a \\'good\\' food!

\-------------------------------------------------------------------------------

alter table syntax:

$sql="alter table tableName add columnName data type";

$query=mysqli\_query($con, $sql);

// $sql="alter table tableName add columnName data type" is used to add a new column in the table.

// $query=mysqli\_query($con, $sql) executes the query.

// "$con" is the connection to MySql server. (See mysqli\_connect()).

e.g.

<?php

$con= mysqli\_connect( "localhost", "root", "12345678" );

if( $con ) {     // if connect MySQL server successfully

echo  " Connect successfully! ";

}

$select=mysqli\_select\_db( $con, "myDB" );

if( $select ) {    // if select database "myDB" successfully

echo  " Select myDB successfully!<br> ";

}      // assume that myDB has a table "colortable"

$sql="alter table colortable add column color5 varchar(20)";

// add a column "color5" into the table, type is "varchar(20)"

$query=mysqli\_query( $con, $sql);     // execute query

if( $query ) {

echo  " Add a column successfully! ";

}

?>

// Output:

Connect successfully!  Select myDB successfully!  
Add a column successfully!

\-------------------------------------------------------------------------------

alter table syntax:

alter table TableName add FieldName type modifier;     // add a field

alter table TableName add primary key (FieldName);     // add a primary key

alter table TableName add unique (FieldName);     // add an unique property

alter table TableName alter FieldName set/drop default;     // alter default value

alter table TableName change FieldName1  FieldName2…;    // change fieldname

alter table TableName drop FieldName;     // remove a field

alter table TableName drop primary key;     // remove a primary key

alter table TableName modify FieldName  type  modifier;   // modify type/modifier

e.g.

use library;

alter table books

add pages int not null,

change author writer char(20);

explain books;

![](image_rsrc70S.jpg)

// “add pages int not null,” adds a new field “pages”.

// “change author writer char(20);” changes the old field name “author” to a new field name “writer”.

// After explaining the table, we can see:

// A new field “pages” has been added.

// The old field name “author” has been changed to new field name “writer”.

\-------------------------------------------------------------------------------

arithmetical operator syntax:

$variable1  operator  $variable2

// Assignment operators are "+, -, \*, /, %, -"

// "%" gets remainder, "-" changes sign or subtracts a value 

e.g.

$x=10;   $y=2;

echo ($x + $y);    // output:  12

echo PHP\_EOL;

echo ($x - $y);     // output:  8

echo PHP\_EOL;

echo ($x \* $y);     // output:  20

echo PHP\_EOL;

echo ($x / $y);     // output:  5

echo PHP\_EOL;

echo ($x % $y);     // output:  0

echo PHP\_EOL;  

echo -$x;         // output:  -10

\-------------------------------------------------------------------------------

array\_change\_key\_case() syntax:

array\_change\_key\_case($array, CASE\_UPPER / CASE\_LOWER)

// Convert all keys in an array to lowercase or uppercase

e.g.

$score=array("Alf"=>"85","Bob"=>"92","Cin"=>"90");

print\_r(array\_change\_key\_case($score,CASE\_UPPER));

// Output:  Array(\[ALF\] => 85    \[BOB\] => 92    \[CIN\] => 90)

\-------------------------------------------------------------------------------

array\_chunk() syntax:

array\_chunk ($array, size)

// Split an array into multiple arrays of a specific size

e.g.

$letter=array ("A", "B", "C", "D", "E", "F"); 

print\_r( array\_chunk($letter,3) );  // each array with 3 elements

// Output:  

Array(

\[0\] => Array( \[0\] => A    \[1\] => B    \[2\] => C )

\[1\] => Array( \[0\] => D    \[1\] => E    \[2\] => F )

)

\-------------------------------------------------------------------------------

array\_combine() syntax:

array\_combine($arr1,$arr2);

// Combine two arrays, arr1 becomes keys, arr2 becomes values

e.g.

$arr1 = array("0","1","2");

$arr2 = array("a","b","c");

$cb = array\_combine($arr1,$arr2);

print\_r($cb);

// Output:   Array( \[0\] => a    \[1\] => b    \[2\] => c )

\-------------------------------------------------------------------------------

array\_count\_values() syntax:

array\_count\_values($arr)

// Return an array using the values as keys, the frequency as values.

e.g.

$arr=array("A","B","C","A","C","C");    // 2A, 1B, 3C

print\_r(array\_count\_values($arr));

// Output:   Array ( \[A\] => 2    \[B\] => 1    \[C\] => 3 )

\-------------------------------------------------------------------------------

array creating syntax:

$arrayName = array ("value0", "value1", "value2",…);

// Create an array with multiple elements

// The index of array starts with zero

e.g.

$arr = array ("A", "B", "C");     // create an array $arr

echo $arr\[0\]; echo $arr\[1\]; echo $arr\[2\];

// Output:   A B C

\-------------------------------------------------------------------------------

array creating syntax:

$arrayName = array ( );

$arrayName\[index0\] = "value0";

$arrayName\[index1\] = "value1";

$arrayName\[index2\] = "value2";

// Create an array with multiple elements

// The index of array starts with zero

e.g.

$color = array( );       // create an array $color

$color\[0\]='red '; $color\[1\]='yellow '; $color\[2\]='green ';

echo "$color\[0\]"; echo "$color\[1\]";echo "$color\[2\]";

// Output:   red  yellow  green

\-------------------------------------------------------------------------------

array\_diff() syntax:

array\_diff($array1,$array2);

// Compare the values of two arrays, return the differences

e.g.

$a1=array("0"=>"a","1"=>"b","2"=>"c","3"=>"d");

$a2=array("4"=>"a","5"=>"b","6"=>"c");

$diff=array\_diff($a1,$a2);

print\_r($diff);

// Output:   Array(\[3\] => d)

\-------------------------------------------------------------------------------

array\_diff\_assoc() syntax:

array\_diff\_assoc($array1,$array2);

// Compare keys and values of two arrays, return the differences

e.g.

$a1=array("0"=>"a","1"=>"b","2"=>"c","3"=>"d");

$a2=array("0"=>"a","1"=>"b","2"=>"c");

$diff=array\_diff\_assoc($a1,$a2);

print\_r($diff);

// Output:   Array(\[3\] => d)

\-------------------------------------------------------------------------------

array\_diff\_key() syntax:

array\_diff\_key($array1,$array2);

// Compare the keys of two arrays, return the differences

e.g.

$a1=array("0"=>"a","1"=>"b","2"=>"c","3"=>"d");

$a2=array("0"=>"a","1"=>"b","2"=>"c");

$diff=array\_diff\_key($a1,$a2);

print\_r($diff);

// Output:   Array(\[3\] => d)

\-------------------------------------------------------------------------------

array\_fill() syntax:

array\_fill(start, number, value)

// Fill an array with the same values.

// "start": the start index, "number": the number of elements.

e.g.

$arr=array\_fill(2,3,"ok");

print\_r($arr);

Output:   Array(\[2\] => ok    \[3\] => ok    \[4\] => ok)

\-------------------------------------------------------------------------------

array\_fill\_keys() syntax:

array\_fill\_keys($keys,"values")

// Fill an array with specified keys and the same values.

e.g.

$keys=array("1","2","3");    // set different keys

$arr=array\_fill\_keys($keys,"ok");

print\_r($arr);

// Output:   Array(\[1\] => ok    \[2\] => ok    \[3\] => ok)

\-------------------------------------------------------------------------------

array\_flip() syntax:

array\_flip($array)

// Flip all keys and their related values in an array

e.g.

$arr=array("1"=>"a","2"=>"b","3"=>"c");

$result=array\_flip($arr);

print\_r($result);

// Output:   Array(\[a\] => 1    \[b\] => 2    \[c\] => 3)

\-------------------------------------------------------------------------------

array\_intersect() syntax:

array\_intersect($array1,$array2);

// Compare all values of two arrays, return an array with the same values.

e.g.

$arr1=array("0"=>"a","1"=>"b","2"=>"c","3"=>"d");

$arr2=array("4"=>"a","5"=>"b","6"=>"c");

$result=array\_intersect($arr1,$arr2);

print\_r($result);

// Output:   Array(\[0\] => a    \[1\] => b    \[2\] => c)

\-------------------------------------------------------------------------------

array\_intersect\_assoc() syntax:

array\_intersect\_assoc($array1,$array2);

// Compare all keys and all values of two arrays, return an array with the same keys and the same values.

e.g.

$arr1=array("0"=>"a","1"=>"b","2"=>"c","3"=>"d");

$arr2=array("0"=>"a","1"=>"b","2"=>"c");

$result=array\_intersect\_assoc($arr1,$arr2);

print\_r($result);

// Output:   Array(\[0\] => a    \[1\] => b    \[2\] => c)

\-------------------------------------------------------------------------------

array\_intersect\_key() syntax:

array\_intersect\_key($array1,$array2);

// Compare all keys of two arrays, return an array with the same keys.

e.g.

$arr1=array("0"=>"a","1"=>"b","2"=>"c","3"=>"d");

$arr2=array("0"=>"e","1"=>"f","2"=>"g");

$result=array\_intersect\_key($arr1,$arr2);

print\_r($result);

// Output:   Array(\[0\] => a    \[1\] => b    \[2\] => c)

\-------------------------------------------------------------------------------

array\_keys() syntax:

array\_keys($array)

// Return all keys of the array.

e.g.

$arr=array("Alf"=>"90","Bob"=>"85","Cin"=>"92");

print\_r(array\_keys($arr));

// Output:   Array(\[0\] => Alf    \[1\] => Bob    \[2\] => Cin)

\-------------------------------------------------------------------------------

array\_key\_exists() syntax:

array\_key\_exists("key", $array)

// Return true if the specified key exists in the array

e.g.

$arr=array("Alf"=>"90","Bob"=>"85","Cin"=>"92");

if (array\_key\_exists("Bob",$arr)){

echo "Bob exists!";

}

// Output:   Bob exists!

\-------------------------------------------------------------------------------

array\_merge() syntax:

array\_merge( array1, array2 );

// Merge array1 and array2, and create a new array.

e.g.

$array1=array ("A", "B", "C");

$array2=array ("D", "E", "F");

$array=array\_merge( $array1, $array2 );     // merge arrays

foreach( $array as $value) { echo("$value " );}

// Output:   A B C D E F

\-------------------------------------------------------------------------------

array\_multisort($arr) syntax:

array\_multisort($arr);

// Return a sorted array in ascending order

e.g.

$arr=array("Cin","Alf","Dan","Bob");

array\_multisort($arr);

print\_r($arr);

// Output:   Array(\[0\]=>Alf   \[1\]=>Bob   \[2\]=>Cin   \[3\]=>Dan)

\-------------------------------------------------------------------------------

array\_pad() syntax:

array\_pad($arrary,size,value)

// Return an array with specified size, the rest array elements will be filled with the parameter value.

e.g.

$arr=array("a","b");

print\_r(array\_pad($arr,4,"c"));  // rest elements will be filled with "c"

// Output:   Array(\[0\] => a    \[1\] => b    \[2\] => c    \[3\] => c)

\-------------------------------------------------------------------------------

array\_pop() syntax:

array\_pop( array );

// Remove the last element of the array.

e.g.

$arr=array("A",  "B", "C", "END");

array\_pop($arr);    // remove the last element

echo ( "$arr\[0\], $arr\[1\], $arr\[2\]" );

// Output:   A, B, C

\-------------------------------------------------------------------------------

array\_product() syntax:

array\_product($array)

// Calculate and return the product of all element values in the array.

e.g.

$arr=array(10,20);

echo(array\_product($arr));

// Output:   200

\-------------------------------------------------------------------------------

array\_push() syntax:

array\_push( array, value1,  value2…);

// array\_push( array, value1,  value2) adds value1, value2  at the end of the array.

e.g.

$arr=array("A", "B", "C");

array\_push($arr, "END");

// add "END" to the end of the array

echo ( "$arr\[0\], $arr\[1\], $arr\[2\], $arr\[3\]" ); 

// Output:   A, B, C, END

\-------------------------------------------------------------------------------

array\_rand() syntax:

array\_rand($array,size)

// Return a new array containing random keys of the original array.

// Parameter size specifies the length of the new array.

e.g.

$arr=array("a"=>"ant","b"=>"bee","c"=>"cat","d"=>"dog");

print\_r(array\_rand($arr,2));

// Output:  Array( \[0\] => b    \[1\] => d )

\-------------------------------------------------------------------------------

array\_reverse() syntax:

array\_reverse($array)

// Return a new array in reversed order

e.g.

$arr=array("1"=>"a","2"=>"b","3"=>"c");

print\_r(array\_reverse($arr));

// Output:   Array( \[0\] => c    \[1\] => b    \[2\] => a )

\-------------------------------------------------------------------------------

array\_search() syntax:

array\_serch("value", $array)

// Search an array for a key according to the array value.

e.g.

$a=array("a"=>"ant", "b"=>"bee", "c"=>"cat", "d"=>"dog");

echo array\_search("cat",$a);     // return a key

// Output:   c

\-------------------------------------------------------------------------------

array\_shift() syntax:

array\_shift( array );

// Remove the first element of the array.

e.g.

$arr=array("START", "A",  "B", "C");

array\_shift($arr);    // remove the first element

echo ( "$arr\[0\], $arr\[1\], $arr\[2\]" );

// Output:   A, B, C

\-------------------------------------------------------------------------------

array size syntax:

count($array);

sizeof($array);

// Two functions can get the size of an array

e.g.

$color = array("yellow", "purple", "orange");

$size1=  count($color);    // get the size of the array

$size2 = sizeof($color);    // get the size of the array

echo ( "$size1  " );     echo ( "$size2  " );

// Output:   3     3

\-------------------------------------------------------------------------------

array\_slice() syntax:

array\_slice( array, start, length );

// Extract some elements from an array, at the start position by specifying length, and create a new array.

e.g.

$array=array("A","B","C","D","E","F");

$arr=array\_slice( $array, 2, 3 );  

// extract three elements from index 2

foreach($arr as $value){ echo "$value ";}

// Output:   C D E

\-------------------------------------------------------------------------------

array\_splice() syntax:

array\_splice($array1, offset, length, $array2)

//  Replace the array1 elements with array2 elements according to the parameter offset and length.

e.g.

$a1=array("a"=>"ant","b"=>"bee","c"=>"cat", "d"=>"dog");

$a2=array("a"=>"awl","b"=>"bat");

array\_splice($a1, 0, 2, $a2);    // replace two elements

print\_r($a1);

// Output:  Array(\[0\]=>awl   \[1\]=>bat   \[c\]=>cat   \[d\]=>dog)

\-------------------------------------------------------------------------------

array\_sum() syntax:

array\_sum($array)

// Return the sum of all element values in an array.

e.g.

$arr=array(10, 20, 30);

echo array\_sum($arr);

// Output:   60

\-------------------------------------------------------------------------------

array\_unique() syntax:

array\_unique($arr)

// Remove all duplicate values from an array

e.g.

$arr=array(10, 20 , 20, 20, 30);

print\_r(array\_unique($arr));

// Output:   Array( \[0\] => 10    \[1\] => 20    \[4\] => 30 )

\-------------------------------------------------------------------------------

array\_unshift() syntax:

array\_unshift( array, value1,  value2…);

// array\_unshift( array, value1,  value2) adds value1, value2  at the beginning of the array.

e.g.

$arr=array("A", "B", "C");

array\_unshift($arr, "START");

// add "START" to the beginning of the array

echo ( "$arr\[0\], $arr\[1\], $arr\[2\], $arr\[3\]" ); 

// Output:   START, A, B, C

\-------------------------------------------------------------------------------

array\_values() syntax:

array\_values($array)

// Return a new array containing all values of the original array.

e.g.

$arr=array("a"=>"ant", "b"=>"bee", "c"=>"cat", "d"=>"dog"); 

print\_r(array\_values($arr));

// Output:   Array(\[0\] => ant    \[1\] => bee    \[2\] => cat    \[3\] => dog)

\-------------------------------------------------------------------------------

arsort() syntax:

arsort($array)

// Sorts an associative array values in descending order.

e.g.

$score=array("Rosy"=>"90","Andy"=>"100","Jony"=>"85");

arsort($score);     // sort values

print\_r($score);

// Output:   Array( \[Andy\] => 100    \[Rosy\] => 90    \[Jony\] => 85 )

\-------------------------------------------------------------------------------

asort() syntax:

asort($array)

// Sorts an associative array values in ascending order.

e.g.

$score=array("Rosy"=>"90","Andy"=>"100","Jony"=>"85");

asort($score);     // sort values

print\_r($score);

// Output:   Array( \[Jony\] => 85    \[Rosy\] => 90    \[Andy\] => 100 )

\-------------------------------------------------------------------------------

assignment syntax:

x += y​is the same as  x = x + y

x -= y​is the same as   x = x - y

x \*= y​is the same as   x = x \* y

x /= y​is the same as   x = x / y

x %= y​is the same as   x = x % y

x .= y​is the same as   x = x . y

e.g.

$a=10; $a += 1; echo $a;   // output 11

$b=20;  $b -= 2; echo $b;   // output 18

$c=30;  $c \*= 3; echo $c;   // output 90 

$d=40;  $d /= 4; echo $d;   // output 10

$e=50;  $e %= 5; echo $e;   // output 0

$f=60; $g=70;  $f.\=$g;  echo $f;    // output 6070

\-------------------------------------------------------------------------------

between…and… syntax:

where FieldName between…and…

// Select records in a certain range in a table.

e.g.

\# 1. Given the current status of the table “books” as follows:

use library;

select \* from books;

![](image_rsrc70T.jpg)

\# 2. Show filtered data by using between…and…

select \* from books where id between 3 and 5;

![](image_rsrc70U.jpg)

//  “where id between 3 and 5;” only selects the id from 3 and 5.

\-------------------------------------------------------------------------------

break statement syntax:

if ( // condition )  break;

// "break" keyword is used to stop the running of a loop according to the condition.

e.g.

<?php

$num=0;

while ($num<10){    

if ($num==5)  break;   // exit the current loop if $num is 5

$num++;

}

echo ( $num );

?>

// Output:   5

\-------------------------------------------------------------------------------

ceil() syntax:

ceil(num)

// Return a closest integer that is greater than or equal to its argument.

e.g.

echo(ceil(9.5));

// Output:   10

\-------------------------------------------------------------------------------

checkbox input syntax:

<input type="checkbox"  name="data" value="myValue">

// type="checkbox" is used to input data by multiple choices.

// name="data" specifies the inputted data that will be passed to the PHP file for processing.

// value="myValue" specifies one of the optional contents.

e.g.

<?php

$data = isset($\_POST\['data'\]) ? $\_POST\['data'\] : "";

if(is\_array($data)) {

$books = array(

'Matlab' => ' Matlab in 8 Hours. ',

'Kotlin' => ' Kotlin in 8 Hours. ',

'Pandas' => ' Pandas in 8 Hours. ',

);

foreach($data as $val) {

echo $books\[$val\] . PHP\_EOL;

}     

} else {

?><form action="" method="post">

<input type="checkbox" name="data\[\]" value="Matlab">Matlab

<input type="checkbox" name="data\[\]" value="Kotlin">Kotlin

<input type="checkbox" name="data\[\]" value="Pandas">Pandas

<input type="submit" value="Submit">

</form>

<?php

}

?>

// Output:

![](image_rsrc70V.jpg)

Kotlin in 8 Hours.    Pandas in 8 Hours.

\-------------------------------------------------------------------------------

chdir() syntax:

chdir("directory");

// Change the working directory to a specified directory

e.g.

echo getcwd() . "\\n";    // get the current working directory

chdir('myDirectory');     // change to myDirectory

echo getcwd() . "\\n";    // get the current working directory

// Output:

/home/study

/home/study/myDirectory

\-------------------------------------------------------------------------------

checkdate() syntax:

checkdate(mm, dd. yyyy)

// Check if a date is valid Gregorian date.  
// The Gregorian date is the internationally accepted civil calendar.

e.g.

var\_dump(checkdate(10, 30, 2022));

var\_dump(checkdate(2, 30, 2021));

// Output:     bool(true)     bool(false)

\-------------------------------------------------------------------------------

chmod() syntax:

chmod(file, mode)

// Change permissions of a file according to the parameter mode.

// The mode parameter has four numbers:

The 1st number is always zero

The 2nd number sets permissions for the owner

The 3rd number sets permissions for the group

The 4th number sets permissions for others

// The mode is set by adding up the following numbers:

1 = executing permissions

2 = writing permissions

4 = reading permissions

e.g.

chmod("myFile.txt",0720);   // Execute, write and read for owner, write for group, nothing for others

chmod("myFile.txt",0604);   // Write and read for owner, nothing for group, read for others.

\-------------------------------------------------------------------------------

chop() syntax:

chop($string, "substring")

// Remove a specified substring in the right end of a string.

e.g.

$str = "Java Cheat Sheet Book";

echo $str."\\n";

echo chop($str,"Book");

// Output:   Java Cheat Sheet

\-------------------------------------------------------------------------------

chr() syntax:

chr(ascii)

// Return a character from the specified ASCII value

e.g.

echo chr(56) . " ";       // Decimal value

echo chr(0x56) . " ";      // Hex value

// Output:   8   V

\-------------------------------------------------------------------------------

chunk\_split() syntax:

chunk\_split($string, length, "separator")

// Split a string according to the specified length and separator.

e.g.

$str = "JavaScript";

echo chunk\_split($str,2,"-");

// Output:   Ja-va-Sc-ri-pt-

\-------------------------------------------------------------------------------

class definition syntax:

class  ClassName{    // define a class

var $variable;     // define a property

function function-name ( ){ }     // define a method

}

// A class is a template for an object, and creates an object.

// The class name is always capitalized

e.g.

class Car {    // define a class "Car"

var speed; var mileage;     // declare two property members

function run( ) {…}      // declare a method member

}

e.g.

<?php

class MyClass{        // define a class

var $p = "A class & object example ";     // define a variable "$p"

}

$obj= new MyClass();    // create an object "obj"

echo $obj \-> p;    // an object references a variable

?>

// Output:   A class & object example

\-------------------------------------------------------------------------------

Class::method() syntax:

Class :: function( );

// A class can use :: to call a function directly.

e.g.

<?php

class A {

function display( ) {

echo "  Display() is called ";

}}

class B extends A {

function show() {

A :: display( );    // class A calls the function display(){ }

echo "  Show() is called  ";

}}

B :: show( );     // class B calls the function show(){ }

?>

// Output:      Display() is called      Show() is called

\-------------------------------------------------------------------------------

clearstatcache();

clearstatcache();

// Clear the cache of the file status

e.g.

<?php    // assume that the original file size is 800 bytes.  
echo filesize("myFile.txt");    // output file size 800 bytes.  
$f = fopen("myFile.txt", "a+");  
ftruncate($f,120);    // truncate the file to 120 bytes  
fclose($f);  
clearstatcache();    // clear cache  
echo filesize("myFile.txt");    // check file size again  
?>

// Output:   800   120

\-------------------------------------------------------------------------------

close connection syntax:

$conn\-\>close();

// Close connection with MySQL.

e.g.

$conn = new mysqli("localhost","user","password","db");

$conn\-\>close();

// The connection will be automatically closed after script finishes running. We can also use "mysqli\_close($conn)" to close connection.

\-------------------------------------------------------------------------------

comment syntax:

//  symbol is used in single-line comments.

/\*……\*/  symbols are used in multi-line comments.

e.g.

echo (" OK ");    // output OK.

echo (" Hello ");   /\* echo ("Hello"); is a PHP output command, "echo" is a PHP reserved word, it shows or prints the word "Hello" in here.  PHP is very easy to learn. \*/

// Output:    OK     Hello

\-------------------------------------------------------------------------------

compact() syntax:

compact("val1", "val2", "val3",…);

// Create a new array by using some variables and values.

e.g.

$a="ant";  $b="bee";  $c="cat";  $d="dog";

$result = compact("a", "b", "c", "d");

print\_r($result);

// Output:   Array( \[a\]=>ant    \[b\]=>bee    \[c\]=>cat    \[d\]=>dog )

\-------------------------------------------------------------------------------

conditional operator syntax:

(test-expression) ? (if-true-do-this) : (if-false-do-this);

// Conditional operator checks if the test-expression is true or false, then, according to true or false to execute the specified block.

e.g.

$a = 100; $b = 200;

$result = ($a<$b) ? "apple " : "banana ";

// (check if $a<$b) ? (if-true-do-this) : (if-false-do-this);

echo ("$result<br>");

// Output:   apple

\-------------------------------------------------------------------------------

connect MySQL syntax:

$con = new mysqli("servername", "username", "password");

// Connect MySQL

e.g.

<?php  
$con = new mysqli("servername", "username", "password");

// Connect MySQL  
if ($con\-\>connect\_error) {   // check connection  
die("Connection fails: " . $con\-\>connect\_error);  
}  
echo "Connection succeeds";  
?>

// Output:   Connection succeeds

\-------------------------------------------------------------------------------

connect\_error() syntax:

$conn \-\> connect\_error

// An connection error happens, and return the error message of the connection with MySQL

e.g.

<?php

$conn = new mysqli("localhost","user","password","db");

if ($conn \-\> connect\_error) {

echo "Failed to connect to MySQL: " . $conn \-\> connect\_error;

exit();

}

?>

// Output:   Failed to connect to MySQL: No connection could be made because the target machine actively refused it.

\-------------------------------------------------------------------------------

const syntax:

const CONSTANT = value;

// The value of constant is immutable in runtime.

e.g.

const NAME = "Ray Yao";     // define a constant

echo NAME;

// Output:   Ray Yao

\-------------------------------------------------------------------------------

constant() syntax:

constant("CONSTANT");

// Return the value of the CONSTANT.

e.g.

define("BOOK", "R in 8 Hours", true);

echo constant("BOOK");

// Output:   R in 8 Hours

\-------------------------------------------------------------------------------

constructor syntax:

function ClassName(){}

// Constructor is used to initialize the class's variables

// The constructor name is always the same as the class name

e.g.

<?php

class Flower{    // define a class "Flower"

var $c;

function Flower( $arg ) {   // define a constructor

$this\-\>c= $arg;   // initialize the variable "c"

}}    

// $this represents the current object $obj

$obj= new Flower( 'beautiful' );     // create an object "$obj"

echo $obj\-\>c;

?>

// Output:  beautiful

\-------------------------------------------------------------------------------

continue statement syntax:

if ( // condition )  continue;

// "continue" is used to stop the current loop according to the condition, ignoring the subsequent code, and then continue the next loop.

e.g.

<?php

$num=0;

while ($num<10){

$num++;

if ($num==5)  continue;   // go to the next loop if $num is 5

echo ( $num );    // skip echo($num) if $num is 5

}     // note:   the output has no the "5"

?>

// output:   1234678910

\-------------------------------------------------------------------------------

copy() syntax:

echo copy("source\_file", "target\_file");

// Copy the source file to the target file.

e.g.  
echo copy("file1.txt","file2.txt");

// If the target file already exists, it will be overwritten.

\-------------------------------------------------------------------------------

count() syntax:

count($array)

// Count the numbers of elements in an array

e.g.

$arr=array("A","B","C");

echo count($arr);

// Output:   3

\-------------------------------------------------------------------------------

count\_chars() syntax:

count\_chars(string, mode)

// Return information about the string according to the following modes:

0 -  an array with ASCII value as key, number of occurrences as value

1 -  an array with ASCII value as key, number of occurrences as value (list number>0)

2 -  an array with ASCII value as key, number of occurrences as value (list number=0)

3 -  a string with all used characters.

4 -  a string with all unused characters.

e.g.

$str = "Hello";

print\_r(count\_chars($str,1));   // use mode 1

// Output:   Array(\[72\] => 1    \[101\] => 1    \[108\] => 2    \[111\] => 1)

// H is 72, e is 101, l is 108, o is 111.

\-------------------------------------------------------------------------------

create database syntax:

CREATE DATABASE dbName

// create a database

e.g.

<?php  
$con = new mysqli("servername", "username", "password");  // connect  
if ($con\-\>connect\_error) {   // check connection  
die("Connection fails: " . $con\-\>connect\_error);  
}  
?>  
$sql = "CREATE DATABASE myDatabase";   // create database  
if ($con\-\>query($sql) === TRUE) {  
  echo "Create a database successfully";  
} else {  
  echo "Create a database unsuccessfully: " . $con\-\>error;  
}  
$con\-\>close();  
?>

// Output:   Create database successfully

\-------------------------------------------------------------------------------

create database syntax:

create database if not exists DatabaseName;

// Create a database in a mysql server

e.g.

create database if not exists garage;

show databases;

![](image_rsrc70W.jpg)

// “create database if not exists garage;” creates a database named “garage” if this database does not exist currently.

\-------------------------------------------------------------------------------

create table syntax:

CREATE TABLE tableName

// Create a table

e.g.

<?php  
$con=new mysqli("servername","username","password","db");  
if ($con\-\>connect\_error) {   // check connection  
die("Connection fails: " . $con\-\>connect\_error);  
}  
$sql = "CREATE TABLE myTable (   // create table  
id INT(8) UNSIGNED AUTO\_INCREMENT PRIMARY KEY,  
firstname VARCHAR(28) NOT NULL,  
lastname VARCHAR(28) NOT NULL,  
)";  
if ($con\-\>query($sql) === TRUE) {  
  echo "Create a table successfully";  
} else {  
  echo " Create a table unsuccessfully: " . $con\-\>error;  
}  
$con\-\>close();  
?>

// Output:   Create a table successfully

\-------------------------------------------------------------------------------

create table syntax:

create table if not exists TableName (col1 type1, col2 type2, …);

// Create a table in the current database

e.g.

use world;

create table if not exists city\_language( id int,  name text );

show tables;

![](image_rsrc70X.jpg)

// “use world;” selects a database "world" before handling with a table.

// “create table if not exists city\_language;” creates a table named “city\_language” if this table does not exist currently.

// "show tables" shows all existing tables in the current database.

\-------------------------------------------------------------------------------

crypt() syntax:

crypt($string);

// Execute a one-way encryption on the string using an algorism.

// Different platforms use different encryptions, such as Des, Md5…

e.g.

$password = "myPassword";

echo crypt($password);    // output will vary

// Output:   $1$fZlP3vyr$gaHN3kr8.O/c9DgIo0GWZ.

\-------------------------------------------------------------------------------

ctype\_alnum() syntax:

ctype\_alnum($string);

// Return true if the string consists of alphanumeric characters.

// Non-alphanumeric characters are <?, <%, <!, #, $, %, ^, &, \* , any other special symbols and spaces.

e.g.

$string = "JAVAin8hours";

if (ctype\_alnum($string)){ echo "It's alphanumeric"; }

// Output:   It's alphanumeric

\-------------------------------------------------------------------------------

ctype\_alpha() syntax:

ctype\_alpha($string);

// Return true if the string consists of alphabetic characters.

// Non-alphabetic characters are 0-9, <?, <%, <!, #, $, %, ^, &, \* , any other special symbols and spaces.

e.g.

$string = "RayYao";

if (ctype\_alpha($string)){ echo "It's alphabetic"; }

// Output:   It's alphabetic

\-------------------------------------------------------------------------------

current() syntax:

current($array)

// Return the element which the current pointer points to, the first element by default.

e.g.

$arr = array("ant", "bee", "cat", "dog");

echo current($arr);

// Output:   ant

\-------------------------------------------------------------------------------

date() syntax:

date("M  d  Y");     // show month, date, year

date( "h : i : s");     // show hour, minute, second

date("D  H  A");     // show day, hour, am/pm

date("d m Y");     // show day, month, year

1.   e.g.

$date = date("M  d  Y ");

$hour = date( "h : i : s ");

$week = date("D  H  A ");

echo $date;  echo $hour;  echo $week;

// Output:   Nov 26 2015 02 : 29 : 02 Thu 14 PM

2.   e.g.

<?php

echo date("Y/m/d") . " ";

echo date("Y.m.d") . " ";

echo date("Y-m-d") . " " ;

?>

// Output:   2022/11/08   2022.11.08    2022-11-08

\-------------------------------------------------------------------------------

dechex() syntax:

dechex(decimal\_number)

// Convert a decimal number into a hexadecimal number.

e.g.

echo dechex("60")." ";

echo dechex("80")." ";

// Output:   3c   50

\-------------------------------------------------------------------------------

define() syntax:

define("NAME", "value", true);

// define a constant and value.

// "NAME": constant name. "value": constant value.

// "true": case insensitive.  "false": case sensitive.

e.g.

define("BOOK", "R in 8 Hours", true);

echo BOOK;    echo "  ";    echo book;

// Output:   R in 8 Hours         R in 8 Hours

\-------------------------------------------------------------------------------

delete record syntax:

DELETE FROM tableName WHERE columnName = value

// Delete a record that meet the condition from a table

e.g.

$sql = "DELETE FROM myTable WHERE id=3";  // php code

// delete a recode where id is 3.

\-------------------------------------------------------------------------------

delete record syntax:

delete from tableName where fieldName = value;

// Remove a record in a table according to "where" statement.

e.g.

delete from myTable where id = 10;     // mysql code

// delete a record whose id is 10.

\-------------------------------------------------------------------------------

describe table syntax:

describe TableName;

// Show a table format, field name, data types and modifiers.

e.g.

use world;

describe city;

![](image_rsrc70Y.jpg)

// “describe city” can show the format of the table “city”.

// Field: Column in the table. (e.g. ID is a column name.)

// Type: Data type of the column. (e.g. The data type of ID is int.)

// Null: Whether allow null or not. (e.g. ID doesn’t allow null.)

// Key: Specify a primary key. (e.g. ID is set as a primary key.)

// Default: Specify a default value. (e.g. ID has no default value.)

// auto\_increment: The field value increases automatically.

\-------------------------------------------------------------------------------

die() syntax:

die("message");

// Output a message and terminate the current program.

e.g.

fopen("myFile.txt","r")    // assume that myFile.txt doesn't exist

or die("The file is no found!");

// Output:   The file is no found!

\-------------------------------------------------------------------------------

do-while loop syntax:

do{ // some php codes in here } while ( test-expression);

// Loops through a block of code once, and then repeats the loop if the specified condition is true.

e.g.

<?php

$counter=0;

do {

echo "@";

$counter++;      // increase 1 every loop

} while ($counter<8);   // loop at most 8 times

?>

// Output:   @@@@@@@@

\-------------------------------------------------------------------------------

drop a field syntax:

alter table TableName drop FieldName;

// Remove a field of a table in a database.

e.g.

\# 1. Given the current status of the table “books” as follows:

use library;

select \* from books;  

![](image_rsrc70Z.jpg)

\# 2. Remove a record and a field.

use library;

delete from books where id = 3;

alter table books drop price;

select \* from books;

![](image_rsrc710.jpg)

// “delete from books where id = 3;” removes a record whose id is 3.

// “alter table books drop price;” removes a field named “price”.

\-------------------------------------------------------------------------------

each() syntax:

// This function has been deprecated since PHP 7.2.0.

\-------------------------------------------------------------------------------

echo syntax:

echo "content";    

echo ("content");

// Output string or value of a variable.

e.g.

echo " Hello World! ";

echo (" Hello World! ");

// Output:   Hello World!   Hello World!

// The different between "echo" and "print":

// "echo" can output one or more strings, without return value.

// "print" only outputs one string and can return a value 1.

\-------------------------------------------------------------------------------

error\_log() syntax:

error\_log(message, Error\_num, destination, header)

// Save an error message to the specified destination on server

// Error number: 0 - send to server, 1 - send by email,

// 2 - send by php3, 3 - send and add to the existing file.

e.g.

error\_log("An error happen!", 3, "/server/tmp/errorFile.log");

// The text will be saved in log.

\-------------------------------------------------------------------------------

empty() syntax:

empty($variable)

// Return true if the $variable is empty, return false if not.

e.g.

$var = 10;     // define a variable

if(empty($var)){echo "'var' is empty.";}

else{ echo "'var' is not empty";}

// Output:   'var' is not empty

\-------------------------------------------------------------------------------

encapsulation syntax:

class MyClass{

private $variable;    // define a private variable

function setVariable(){…}    // set the variable value

function getVariable(){…}    // get the variable value

}

// Encapsulation can hide the sensitive information from the user, ensure the security.

// Encapsulation wraps the similar properties and methods together in a single unit called class.

e.g.

<?php

class Income{     // encapsulation

private $salary;     // define a private variable

public function setSalary($arg){

$this\-\>salary = $arg;

}

public function getSalary(){

return $this\-\>salary;

}

};

$m = new Income();

$m\-\>setSalary(98000);

echo "Salary is $".$m\-\>getSalary()." dollars per month";

?>

// Output:   Salary is $98000 dollars per month

\-------------------------------------------------------------------------------

enctype syntax:

<form enctype="value">

// Specify which content type to use when submitting the form.

e.g.

<form  enctype = "multipart/form-data">

// For unloading a file or submitting file data

<form  enctype \= "text/plain">

// Send data without any encoding

\-------------------------------------------------------------------------------

end() syntax:

end($array)

// Return the last element of an array.

e.g.

$arr = array("ant", "bee", "cat", "dog");

echo end($arr);

// Output:   dog

\-------------------------------------------------------------------------------

explain table syntax:

explain TableName;

// Show a table format, field name, data types and modifiers.

e.g.

use world;

explain city;

![](image_rsrc70Y.jpg)

// “explain city” can show the format of the table “city”.

// Field: Column in the table. (e.g. ID is a column name.)

// Type: Data type of the column. (e.g. The data type of ID is int.)

// Null: Whether allow null or not. (e.g. ID doesn’t allow null.)

// Key: Specify a primary key. (e.g. ID is set as a primary key.)

// Default: Specify a default value. (e.g. ID has no default value.)

// auto\_increment: The field value increases automatically.

\-------------------------------------------------------------------------------

exit() syntax:

exit("message");

// Output a message and exit the current program.

e.g.

fopen("myFile.txt","r")    // assume that myFile.txt doesn't exist

or exit("The file is no found!");

// Output:   The file is no found!

\-------------------------------------------------------------------------------

explode() syntax:

explode(separator,$str)

// Convert a string into an array

e.g.

$str = "R in 8 hours";

print\_r (explode(" ",$str));

// Output:   Array( \[0\]=>R    \[1\]=>in    \[2\]=>8    \[3\]=>hours )

\-------------------------------------------------------------------------------

extends syntax:

class sub-class  extends  parent-class {……}

// The child class can inherit all features of the parent class.

// The object of child class can reference the variable and function of the parent class.

e.g.

<?php

class Animal{     // parent class

var $head;     // parent class's variable

function tail( ) {     // parent class's function

echo " Dog's tail is small ";

}}

class Dog extends Animal{ // child class inheritance parent class

}

$d = new Dog( );     // create an object of the child class

$d\-\>head = "big"; // references the variable of the parent class

echo " Dog's head is ".$d\-\>head." ";

$d\-\>tail( );    // references the function of the parent class

?>

// Output:     Dog's head is big      Dog's tail is small

\-------------------------------------------------------------------------------

eval() syntax:

eval($string)

// Evaluate a string as PHP code. The string must be valid PHP code and must end with semicolon.

e.g.

$str = '$num = 100; echo $num;';

eval($str);    // the $str is php code

// Output:   100

\-------------------------------------------------------------------------------

exec() syntax:

exec('external\_program');

// Execute an external program or an external command.

e.g.

echo exec('whoami');

// The function will return the last line of the executed program's output.

\-------------------------------------------------------------------------------

extract() syntax:

extract($array);

// Convert array keys into variable names and array values into variable value.

e.g.

$arr=array("a"=>"ant", "b"=>"bee", "c"=>"cat", "d"=>"dog");

extract($arr);

echo "\\$a=$a; \\$b=$b; \\$c=$c; \\$d=$d";

// Output:   $a=ant; $b=bee; $c=cat; $d=dog

\-------------------------------------------------------------------------------

fclose() syntax:

fcolse($openedFile);   

// Close the opened file

// Release memory resource, other processes using the file

e.g.

$filename = "D:\\myfile.txt";     // set the path D:\\myfile.txt

$openfile = fopen( $filename, w );    // open a file with w mode

$content = fwrite( $openfile, "Hello!!" );    // writing

fcolse($openfile);    // close the opened file  

// After writing myfile.txt, we can use fclose() to close the opened file.

\-------------------------------------------------------------------------------

feof() syntax:

feof($file)

// Return true if reading reaches the end of file, return false if not.

e.g.

$f = fopen("myFile.txt","r");

while( !feof($f) ){   // If don't read to the end of the file, keep running

$contents = fgets($f);    // fgets($f) reads the file

echo $contents. "<br>";

}

// Output:     ( The following text is the contents of the file )

Hi, this is myfile.txt, there are two lines in this file.  
Here is the end of the file.

\-------------------------------------------------------------------------------

fgetc() syntax:

fgetc($file)

// Read one character from the specified file

e.g.  
$f = fopen("myFile.txt","r");  
echo fgetc($f);

// Output:    R

\-------------------------------------------------------------------------------

fgetcvs() syntax:

fgetcvs($file)

// Read one line from the cvs file

e.g.  
$f = fopen("myFile.cvs","r");  
print\_r(fgetcsv($f));

// Output:  Array(\[0\]=>ant  \[1\]=>bee  \[2\]=>cat  \[3\]=>dog)

\-------------------------------------------------------------------------------

fgets() syntax:

fgets($file)

// Read one line from the specified file

e.g.  
$f = fopen("myFile.txt","r");  
echo fgets($f);

// Output:    This is one line text in myFile.txt

\-------------------------------------------------------------------------------

file() syntax:

file("filename.txt")

// Read the contents of a file to an array

e.g.  
print\_r( file("myFile.txt") );

// Output:   Array ( \[0\]=>Hi, this is myFile.txt.  \[1\]=>There are two lines in this file.   \[2\]=>Here is the last line. )

\-------------------------------------------------------------------------------

fileatime() syntax:

fileatime("file.txt"))

// Return the last access time of the specified file

e.g.

echo "Last access: ".date("F d Y H:i:s.", fileatime("myFile.txt"));

// Output:   Last access: May 17 2022 18:15:32.

\-------------------------------------------------------------------------------

filemtime() syntax:

filemtime("file.txt"))

// Return the last modifying time of the specified file

e.g.

echo "Last modified: ".date("F d Y H:i:s.", filemtime("d:\\myFile.txt"));

// Output:   Last access: May 17 2022 18:15:32.

\-------------------------------------------------------------------------------

file uploading syntax:

<input type="file" name="file">

// input type="file" specifies the form that is used to upload file.

// name="file" specifies the uploaded "file" that will be passed to the PHP file for processing.

e.g.   // Assume that we upload a file named "myFile.txt"

<form action="" method="post" enctype="multipart/form-data">

<input type="file" name="file">

<input type ="submit" value="Submit">

</form>

<?php

echo "File Name: " . $\_FILES\['file'\]\['name'\]."<br>";

echo "File Type : " . $\_FILES\['file'\]\['type'\]."<br>";

echo "File Size : " . $\_FILES\['file'\]\['size'\]."<br>";

echo "Temp Name: " . $\_FILES\['file'\]\['tmp\_name'\]."<br>";

echo "Error Info: " . $\_FILES\['file'\]\['error'\]. "<br>";

?>

// Output:  

![](image_rsrc70N.jpg)

File Name: myFile.txt  
File Type : text/plain  
File Size : 279  
Temp Name: C:\\Windows\\Temp\\php5167.tmp  
Error Info: 0

\-------------------------------------------------------------------------------

file\_exists() syntax:

file\_exists("myFile.txt")

// Return true if the file exists, return false if not.

e.g.

$f = 'myFile.txt';    // assume that myFile.txt doesn't exist

if ( file\_exists($f)) { echo "The file $f exists"; }

else { echo "The file $f does not exist"; }

// Output:   The file myFile.txt does not exist

\-------------------------------------------------------------------------------

filesize() syntax:

filesize("file.txt")

// Return the size of a file

e.g.  
echo filesize("myFile.txt");

// Output:   98

\-------------------------------------------------------------------------------

file\_get\_contents() syntax:

file\_get\_contents("myFile.txt");

// Read the contents of the file.

e.g.  
echo file\_get\_contents("myFile.txt");

// Output:   Hi, this is myFile.txt, How are you?

\-------------------------------------------------------------------------------

file\_put\_contents() syntax:

file\_put\_contents("myFile", "contents");

// Write the contents to the file, and return the length.

e.g.

echo file\_put\_contents("myFile.txt", "Hi, this is myFile.txt.");

// Output:   23

\-------------------------------------------------------------------------------

filter\_callback syntax:

FILTER\_CALLBACK, array("options"=>function)

// Call a user-defined function or built in function to filter the value.

// FILTER\_CALLBACK is the parameter of filter\_var()

e.g.

$str="jquery in 8 hours";

echo filter\_var($str, FILTER\_CALLBACK,

array("options"=>"strtoupper"));  // call built-in function "strtoupper"

// Output:   JQUERY IN 8 HOURS

\-------------------------------------------------------------------------------

filter\_has\_var() syntax:

filter\_has\_var(type, "variable")

// Check if the form input has the specified value

// type:  INPUT\_GET,   INPUT\_POST,  INPUT\_COOKIE,   INPUT\_SERVER,   INPUT\_ENV

// variable: an external variable from the form input

e.g.

// assume that we didn't input url in the form

if (!filter\_has\_var(INPUT\_POST, "url")){

echo("URL not found");} else {

echo("URL found");}

// Output:   URL not found

\-------------------------------------------------------------------------------

filter\_input syntax:

filter\_input(type, variable, filter)

// Get an external variable from the form input and filter it.

// type:  INPUT\_GET,   INPUT\_POST,  INPUT\_COOKIE,   INPUT\_SERVER,   INPUT\_ENV

// variable:  an external variable from the form input

// filter:  various filters (see Filter Chart)

e.g.

if(isset($\_POST\["email"\])){    // assume that we input xxx@yyy.com

if(filter\_input(INPUT\_POST, "email", FILTER\_VALIDATE\_EMAIL)===false){

echo("Email format is not valid"); } else {

echo("Email format is valid"); }

}

// Output:   Email format is valid

\-------------------------------------------------------------------------------

filter\_input\_array() syntax:

filter\_input\_array(type, $array)

// Get multiple external variables from the form input and filter them.

// type:  INPUT\_GET,   INPUT\_POST,  INPUT\_COOKIE,   INPUT\_SERVER,   INPUT\_ENV

// $array:  multiple external variables from the form input

e.g.

$arr = array (    // assume that we input Ray Yao and 28 in the form

"name" => array ("filter"=>FILTER\_CALLBACK,),

"age"   => array ( "filter"=>FILTER\_VALIDATE\_INT,),

);   // "filter" refers to various filters (see Filter Chart)

print\_r(filter\_input\_array(INPUT\_POST, $arr));

// Output:

Array(  
  \[name\] => Ray Yao  
  \[age\] => 28  
)

\-------------------------------------------------------------------------------

filter\_var() syntax:

filter\_var($variable, filter)

// Filter a variable with the specified filter

// "filter" refers to a built in filter in php. (see Filters Chart)

e.g.

$email = "xxx123@demo.com";

if (filter\_var($email, FILTER\_VALIDATE\_EMAIL))

// FILTER\_VALIDATE\_EMAIL is a filter to validate email address

{ echo("$email is a valid email address");}

else {echo("$email is not a valid email address");}

// Output:   xxx123@demo.com is a valid email address

\-------------------------------------------------------------------------------

filter\_var\_array() syntax:

filter\_var\_array($array)

// Get multiple variables and values.

e.g.

$arr = array(

'A' => 'Apple',

'B' => 'Banana',

);

$fruit = filter\_var\_array($arr);

var\_dump($fruit);

// Output: array(2){\["A"\]=>string(5)"Apple"   \["B"\]=>string(6)"Banana"}

\-------------------------------------------------------------------------------

final syntax:

final class BaseClass{…}

final public function myFun(){…}

// final class cannot be extended, final function cannot be overridden.

e.g.

<?php

final class BaseClass {

final public function myFun() {

echo "We are final class and final function";

}}

class ChildClass extends BaseClass {    // error

public function myFun() {     // error

echo "Try to extend final class & override final method" ;

}}

?>

// final class cannot be extended, final function cannot be overridden.

\-------------------------------------------------------------------------------

floatval() syntax:

floatval($data)

// Return a float value

e.g.

$data = "123.456Good!";

echo floatval($data);

// Output:   123.456

\-------------------------------------------------------------------------------

floor() syntax:

floor(number)

// Return a closest integer that is less than or equal to its argument.

e.g.

echo(floor(9.5));

// Output:   9

\-------------------------------------------------------------------------------

flush() syntax:

flush();

// Push all output to the browser as quick as possible instead of waiting till the whole program has completed, which can speed up the website.

e.g.

<?php

for($num=0; $num<100; $num++){

echo $num;

flush();

}

// assume that there are long long codes in here……

?>

// Output:  12345678……100

\-------------------------------------------------------------------------------

fopen() syntax:

fopen($filename, mode);

// Open a file in a specified mode. The mode to open a file is:

| Mode || Operation |
| --- | --- |
| r || open file for reading only, read from the beginning. |
| w || open file for writing only, clear original content. |
| a || open file for writing only, append new content. |
| x || create a new file for writing only. |

// Note: If above modes with "+" sign, it means opening the file for both reading and writing. e.g. r+, w+, a+, x+

e.g.

$filename = "myfile.txt";

fopen( $filename, r );    // open the file for reading only

fopen( $filename, w );    // open the file for writing only

fopen( $filename, a+ );    // open the file for both writing and reading, append new content to the end when writing.

\-------------------------------------------------------------------------------

for loop syntax:

for( init, test-expression, increment) { // some codes; }

// "init" initializes a variable that is used to control the loop.

// "test-expression" allows to loop if it returns true.

// "increment" will increase 1 after every loop

e.g.

for ($x = 0; $x <= 5; $x++) {   // loop at most 5 times

echo "$x ";

}

// Output:   012345

\-------------------------------------------------------------------------------

foreach() syntax:

foreach( $array as $key=>$value ){ }

// foreach() can iterate over all elements of an array.

e.g.

$book=array( "A"=>"JSP", "B"=>"ASP", "C"=>"PHP");

foreach ( $book as $key => $value ){      // iteration

echo "The  $key  book is about  $value. <br>";

}      // $key stores all keys, $value stores all values

// Output:  

The A book is about JSP.

The B book is about ASP.

The C book is about PHP.

\-------------------------------------------------------------------------------

fprintf() syntax:

fprintf($file," %format", $variable);

// Write a formatted string to a file.

// Replace the %format with the value of $variable

// About %format, please see The String Format Chart.

e.g.

$num = 8;   $str = "Hours";

$file = fopen("d:\\myFile.txt","w");

fprintf($file,"JAVA in %u %s.", $num, $str);

// $num replaces %u. $str replaces %s

// Please check myFile.txt

// The content of the myFile.txt is:   JAVA in 8 Hours

\-------------------------------------------------------------------------------

fputs() syntax:

// fputs() is an alias of the fwrite(), please see fwrite().

\-------------------------------------------------------------------------------

fread() syntax:

fread( $openfile, length );

// "fread()" reads the content of a file.

// "$openfile" specifies the opened file for reading.

// "length" specifies the maximum number of bytes to read.

e.g.

// Given the content of myfile.txt is: "Hello!"

// the path of the myfile.txt is: D:\\myfile.txt

$filename = "D:\\myfile.txt";

$openfile = fopen( $filename, r );    // open a file with r mode

$content = fread( $openfile, 20 );    // read 20 bytes

echo "$content";   

// Output:   Hello!

\-------------------------------------------------------------------------------

fscanf() syntax:

fscanf($file, "%format");

// Parse a file according to the specified format

// About %format, please see The String Format Chart.

e.g.

// Assume that the contents of myFile.txt is as follows:

Andy   Student   17

$file = fopen("myFile.txt", "r");

$array = fscanf($file, "%s \\t %s \\t %d");

print\_r($array);

// Output:   Array( \[0\]=>Andy   \[1\]=>Student   \[2\]=>17 )

\-------------------------------------------------------------------------------

ftruncate() syntax;

ftruncate($file, size);

// Truncates an open file to the specified size (bytes).

e.g.

<?php    // assume that the original file size is 800 bytes.  
echo filesize("myFile.txt");    // output file size 800 bytes.  
$f = fopen("myFile.txt", "a+");  
ftruncate($f,120);    // truncate the file to 120 bytes  
fclose($f);  
clearstatcache();    // clear cache  
echo filesize("myFile.txt");    // check file size again  
?>

// Output:   800   120

\-------------------------------------------------------------------------------

function syntax:

function functionName ( ) {……}     // define a function

functionName ( );     // call the function

e.g.

<?php

function test( ){     // declare a function

echo ("show a sample");    // output

}

test ( );     // call the function

?>

// Output:   show a sample

\-------------------------------------------------------------------------------

function with argument syntax:

function functionName($argument) {……}    // define a function

functionName(parameter);  // call the function and pass parameter

e.g.

<?php

function test( $arg ){   // declare a function with arguments

echo ("$arg");

}

test("display a sample");  // call the function, and pass args.

?>

// Output:   display a sample

\-------------------------------------------------------------------------------

fwrite() syntax:

fwrite( $openfile, "contents");

// "fwrite( )" writes the contents to a file.

// "$openfile" specifies the opened file for writing.

// "contents" specifies the contents to write.

e.g.

$filename = "D:\\myfile.txt";     // set the path D:\\myfile.txt

$openfile = fopen( $filename, w );    // open a file with w mode

$content = fwrite( $openfile, "Hello!" );   // writing

echo "Write a file successfully!";

// Output:   Write a file successfully!

// If you open D:\\myfile.txt, you can see the content "Hello!".

\-------------------------------------------------------------------------------

getcwd() syntax:

getcwd();

// Return the current working directory.

e.g.  
echo getcwd();

// Output:  /home/phpdirectory

\-------------------------------------------------------------------------------

getdate() syntax:

getdate();

// Return the information of the local date and time.

e.g.  
print\_r(getdate());

// Output:   Array( \[seconds\]=>26  \[minutes\]=>38 ….. \[year\]=>2022 )

\-------------------------------------------------------------------------------

get\_resource\_type() syntax:

get\_resource\_type($resource);

// Return the resource type

e.g.  
$file = fopen("myFile.txt","r");  
echo get\_resource\_type($file);

// Output:   stream

\-------------------------------------------------------------------------------

getenv() syntax:

getenv("VARIABLE");

// Get the value of an environment variable.

e.g.

putenv("USER=Ray Yao");

echo "The user name is: " . getenv("USER");

// Output:   The user name is: Ray Yao

\-------------------------------------------------------------------------------

getFile() syntax:

$e\-\>getFile()

// Output the file in which the exception occurs.

e.g.

try {

throw new Exception("An exception occurs!");

} catch(Exception $e) {

echo "Exception occurs in this file: ".$e\-\>getFile();

}

// Output:   Exception occurs in this file: /server/script.php

\-------------------------------------------------------------------------------

getLine() syntax:

$e\-\>getLine()

// Output the number of the line on which the exception was thrown

e.g.

try {

throw new Exception("An error occurs!");

} catch(Exception $e) {

echo "Exception occurs in this line: ".$e\-\>getLine();   

}

// Output:   Exception occurs in this line: 3

\-------------------------------------------------------------------------------

getMessage() syntax:

$e\-\>getMessage()

// Output the exception message.

e.g.

try {

throw new Exception("An exception occurs!");

} catch(Exception $e) {

echo $e\-\>getMessage();

}

// Output:   An exception occurs!

\-------------------------------------------------------------------------------

global variable syntax:

$variable=value;  function funName(){ global $variable }

// A global variable is declared outside the function, it can be used in everywhere;

// If a global variable is used inside a function, the variable should be prefixed a keyword "global"

e.g.

<?php

$x = 100;    $y = 200;    // global variable

function myFun(){

global $x, $y;    // use two global variables inside a function

$y = $x + $y;

echo $y;

}

myFun();

?>

// Output:   200

\-------------------------------------------------------------------------------

gmdate() syntax:

gmdate(format, timestamp)

// Format the local GMT/UTC date/time in the specified format.

// About data/time format, please see Data Time Format Chart.

e.g.

echo gmdate("Y F jS l h:i:s a");

// Output:   2022 November 16th Wednesday 06:08:20 pm

\-------------------------------------------------------------------------------

gmmktime() syntax:

gmmktime(hour, minute, second, month, day, year)

// Return the Unix timestamp for the given GMT date.

e.g.

echo date("M-d-Y", gmmktime(0, 0, 0, 1, 1, 2018))."  ";

echo date("M-d-Y", gmmktime(0, 0, 0, 10, 10, 2022));

// Output:    Jan-01-2018   Oct-10-2022

\-------------------------------------------------------------------------------

header syntax;

header("string\_to\_send");

// Send a HTTP header to a client before some other outputs

e.g.

header('Location: url'); 

// Redirect the current web page to another web page.

header("Cache-Control: no\_cache");

// Indicate that browser must always reload this page without cache.

header("HTTP/1.0 404 Not Found");

// Set HTTP Status in the header response.

e.g.

<?php

header( "Location:http://www.amazon.com");  // to Amazon

?>

// Output:   (We can see the home page of Amazon)

\-------------------------------------------------------------------------------

heredoc syntax:

$var= <<<EOF

texts

EOF;

// Heredoc is a way to write large amounts of text in PHP code without the single quote, double quote delimiters.

// Heredoc starts with <<<EOF and ends with EOF; End tag must have no indentation or spaces, and must have a semicolon.

e.g.

$book="C# in 8 Hours";

$var= <<<EOF

The book is:  $book

EOF;     

echo $var;

// Output:     The book is:  C# in 8 Hours

\-------------------------------------------------------------------------------

htmlentities() syntax:

htmlentities($characters)

// Convert characters to html entities

e.g.

$str = '<a href="https://www.amazon.com">Amazon</a>';

echo htmlentities($str);

// Output:   &lt;a href=&quot;https://www.amazon.com&quot;&gt;Amazon&lt;/a&gt;

\-------------------------------------------------------------------------------

html\_entity\_decode() syntax:

html\_entity\_decode($html\_entities);

// Convert html entities to characters.

e.g.

$str = '&lt;a href=&quot;https://www.amazon.com&quot;&gt;Amazon&lt;/a&gt;';

echo html\_entity\_decode($str);

// Output:   <a href="https://www.amazon.com">Amazon</a>

\-------------------------------------------------------------------------------

htmlspecialchars() syntax:

htmlspecialchars($predefined\_characters);

// Convert predefined characters to html entitles.

// About predefined characters, please see Predefined Chars Chart

e.g.

$str = 'Here is a "<i>italic</i>" text.';

echo htmlspecialchars($str);

// Output:   Here is a &quot;&lt;i&gt;italic&lt;/i&gt;&quot; text.

\-------------------------------------------------------------------------------

htmlspecialchars\_decode() syntax:

htmlspecialchars\_decode($html\_entities);

// Convert html entities to predefined characters.

// About predefined characters, please see Predefined Chars Chart

e.g.

$str = 'Here is a &quot;&lt;i&gt;italic&lt;/i&gt;&quot; text.';

echo htmlspecialchars\_decode($str);

// Output:   Here is a "<i>italic</i>" text.

\-------------------------------------------------------------------------------

http\_build\_query() syntax:

http\_build\_query($data)

// Generate a URL-encoded query string from an array.

e.g.

$data=array("a"=>"ant", "b"=>"bee", "c"=>"cat", "d"=>"dog");

echo http\_build\_query($data);

// Output:   a=ant&b=bee&c=cat&d=dog

\-------------------------------------------------------------------------------

iconv() syntax:

iconv( $input\_charset, $output\_charset, $str );

// Convert a string to requested character encoding. 

e.g.

$str = " EURO '€' ";

echo 'Original :', ("$str"), PHP\_EOL;

echo 'Translated :', iconv("UTF-8", "ISO-8859-1//TRANSLIT", $str);

// Output:

Original : EURO '€'

Translated : EURO 'EUR'

\-------------------------------------------------------------------------------

if statement syntax:

if ( test-expression ) {   // if true do this;   }

// "if statement" executes codes inside { … } only if a specified condition is true, does not execute any codes inside {…} if the condition is false.

e.g.

$x = 200;  $y = 100;

if ( $x > $y ){    // if true, run following code

echo "x is greater than y."; 

}

// Output:   x is greater than y.

\-------------------------------------------------------------------------------

if-else Statement syntax:

if ( test-expression){   // if true do this;   }

else {  // if false do this;   }

// "if...else statement" runs a part of codes if the test returns true or runs other part of codes if the test returns false.

e.g.

<?php

$x = 100; $y = 200;   

if ( $x > $y ){    // if true, run this code block

echo "x is greater than y.";

}

else {   // if false, run this code block

echo "x is less than y";

}

?>  

// Output:   x is less than y

\-------------------------------------------------------------------------------

if…elseif…else syntax:

if (condition){ // if\_true\_do\_this }

elseif(condition){ // otherwise, if\_true\_do\_this }

else{ // if\_false\_do\_this }

e.g.

$h=date("H");

if ($h<"11"){ echo "Good morning!"; }

elseif ($h<"19"){ echo "Good day!"; }

else{ echo "Good night!"; }

// Output:   Good morning!

\-------------------------------------------------------------------------------

implode() syntax:

implode(separator, $array)

// Join array elements with a string

e.g.

$arr = array('Scala' , 'in' , '8' , 'Hours');

echo implode(" \*  ", $arr);

// Output:   Scala \*  in \*  8 \*  Hours

\-------------------------------------------------------------------------------

in\_array() syntax:

in\_array("element", $arr)

// Return true if the specified element is in the array, return false if not.

e.g.

$arr = array("ant", "bee", "cat", "dog");

if (in\_array("cat", $arr)){

echo "The 'cat' is in the array";

}

// Output:   The 'cat' is in the array

\-------------------------------------------------------------------------------

include() syntax:

include( "anotherFile.php" )    

// Import the code from another.php to the current file

// "include()" is usually in the middle of the file, if the program has an error, a message will appear, but the program will keep going.

e.g.

1.   <!\-\-file1.php\-\->

<?php   echo " From file1.php ";  ?>

2.   <!\-\-file2.php\-\->

<?php  

echo " From file2.php ";

include("file1.php");    // import file1.php to here

?>

// Output:     From file2.php     From file1.php    

\-------------------------------------------------------------------------------

include\_once() syntax:

include\_once( "anotherFile.php" )    

// Import the code from another.php to the current file for only once.

// "include\_once()" is usually in the middle of the file, if the program has an error, a message will appear, but the program will keep going.

e.g.

1.   <!\-\-file1.php\-\->

<?php   echo " From file1.php ";  ?>

2.   <!\-\-file2.php\-\->

<?php  

echo " From file2.php ";

include\_once("file1.php");    // import file1.php to here once

?>

// Output:     From file2.php     From file1.php    

\-------------------------------------------------------------------------------

insert into table syntax:

INSERT INTO tableName (fieldnames) VALUES ('data')

// Add new records to a MySQL table by inserting data

// Note: In the PHP code, if we use MySQL command to insert strings into a table, the strings should be enclosed by \\" symbols.

e.g.

<?php  
$con=new mysqli("servername","username","password","db");  
if ($con\-\>connect\_error) {   // check connection  
die("Connection fails: " . $con\-\>connect\_error);  
}  
echo "Connection succeeds";  
?>

$sql = "INSERT INTO myTable (firstname, lastname) VALUES (\\"Andy\\", \\"Smith\\")";  
if ($con\-\>query($sql) === TRUE) {  
  echo "Insert data successfully";  
}  
?>

// Output:   Connection succeeds      Insert data successfully

\-------------------------------------------------------------------------------

insert into table syntax:

$sql="insert into tableName (columns) values ("data")";

$query=mysqli\_query($con, $sql);    // execute the query

// $sql="insert into tableName (columns) value ("data")" is used to insert data into a table. Note: In the PHP code, if we use MySQL command to insert strings into a table, the strings should be enclosed by \\" symbols.

// "$con" is the connection to MySql server. (see mysqli\_connect()).

e.g.

<?php

$con= mysqli\_connect( "localhost", "root", "12345678" );

if( $con ) {     // if connect MySQL server successfully

echo  " Connect successfully! ";

}

$select=mysqli\_select\_db( $con, "myDB" );

if( $select ) {    // if select database "myDB" successfully

echo  " Select myDB successfully!<br> ";

}      // assume that myDB has a table "colortable"

$sql="insert into colortable (color1, color2, color3, color4) values (\\"pink\\",\\"navy\\",\\"purple\\",\\"orange\\")"; 

// insert four strings data into the four columns of the table

$query=mysqli\_query( $con, $sql);   // execute query

if( $query ) {

echo  "Insert data successfully! ";

}

?>

// Output:

Connect successfully!  Select myDB successfully!

Insert data successfully!

\-------------------------------------------------------------------------------

insert into table syntax:

insert into TableName (field1, field2, field3, …)

values (value1, value2, value3, …);

// Insert data to a table in a database

e.g.

use library;

insert into books(title, price, author)

values("Java", 13.99, "Ray Yao");

insert into books(title, price, author)

values("Html", 12.88, "Ann Lee");

insert into books(title, price, author)

values("Lamp", 11.67, "Jan Poe");

// “insert into books(title, price, author) values("Java", 13.99, "Ray Yao");” will insert three values "Java", 13.99, "Ray Yao" into associated three fields “title, price, author”.

// Three records are being inserted to a table "books" in the "library".

\-------------------------------------------------------------------------------

intdiv() syntax:

intdiv(num1, num2)

// num1 divides num2, and convert the result to an integer

e.g.

var\_dump(intdiv(100, 33));

// Output:   3

\-------------------------------------------------------------------------------

interface syntax:

interface interfaceName{method();}

class ClassName implements InterfaceName{method(){}}

// With interfaces, you can specify which methods a class must implement, Interfaces are defined by the interface keyword.

// A class can implement the interface. Interface method has no body.

// The method of the class can override the method of the interface.

e.g.

<?php

interface Animal {    // define an interface

public function roar();    // define a method with body

}

class Dog implements Animal {     // implement the interface

public function roar() {

echo "WOW, WOW, WOW";

}}

$d = new Dog();

$d\-\>roar();

?>

// Output:   WOW, WOW, WOW

\-------------------------------------------------------------------------------

is\_dir() syntax:

is\_dir($variable)

// Return true if the $variable is a directory.

e.g.

$d = "d:\\myFolder";

if (is\_dir($d)){ echo ("$d a directory.");}

// Output:   myFolder is a directory.

\-------------------------------------------------------------------------------

is\_file() syntax:

is\_file($variable)

// Return true if the $variable is a file.

e.g.  
$f = "myFile.txt";  
if(is\_file($f)) { echo ("$f is a file.");}

// Output:   myFile.txt is a file.

\-------------------------------------------------------------------------------

is\_int() syntax:

is\_int($variable)

// Return true if the $variable is an integer.

e.g.

$num = 168;

if(is\_int($num)){ echo "$num is an integer.";}

// Output:   168 is an integer.

\-------------------------------------------------------------------------------

is\_integer() syntax:

// is\_integer is an alias of in\_int(), please see is\_int().

\-------------------------------------------------------------------------------

is\_null() syntax:

is\_null($variable)

// Return true if the $variable is null.

e.g.

$var1 = null; if(is\_null($var1)){ echo " var1 is null. ";}

$var2 = NULL; if(is\_null($var2)){ echo " var2 is null. ";}

// Output:   var1 is null.  var2 is null.

\-------------------------------------------------------------------------------

is\_numeric() syntax:

is\_numeric($variable)

// Return true if the $variable is a numeric string or a number.

e.g.

$var = "168";

if(is\_numeric($var)){ echo "$var is a numeric string or a number";}

// Output:   168 is a numeric string or a number

\-------------------------------------------------------------------------------

is\_readable() syntax:

is\_readable($variable)

// Return true if the $variable is a readable file.

e.g.  
$f = "myFile.txt";  
if(is\_readable($f)) { echo ("$f is a readable file.");}

// Output:   myFile.txt is a readable file.

\-------------------------------------------------------------------------------

is\_string() syntax:

is\_string($variable)

// Return true if the $variable is a string.

e.g.

$var = "CHARACTERS";

if(is\_string($var)){ echo "$var is a string.";}

// Output:   CHARACTERS is a string.

\-------------------------------------------------------------------------------

isset() syntax:

isset($variable)

// Return true if the $variable is set a value, return false if not.

e.g.

$var = 10;

if (isset($var)) {    // return true if $var is set a value

echo "The var is set";

}

// Output:   The var is set

\-------------------------------------------------------------------------------

is\_executable() syntax:

is\_executable($file)

// Return true if the $file is executable.

e.g.

$f = "config.exe";

if(is\_executable($f)){echo ("$f is executable.");}

// Output:   config.exe is executable.

\-------------------------------------------------------------------------------

is\_writable() syntax:

is\_writable($variable)

// Return true if the $variable is a writable file.

e.g.  
$f = "myFile.txt";  
if(is\_writable($f)) { echo ("$f is a writable file.");}

// Output:   myFile.txt is a writable file.

\-------------------------------------------------------------------------------

is\_writeable() syntax:

// is\_writeable() is an alias of is\_writable(), please see is\_writable()

\-------------------------------------------------------------------------------

json\_decode() syntax:

json\_decode($json, bool)

// Convert a JSON encoded object into a PHP variable

// If "bool" arg is true, convert an json format to an array format.

e.g.

$json = '{"a":6, "b":3, "c":8}';

var\_dump(json\_decode($json, true));

// Output:   array(3){ \["a"\]=>int(6) \["b"\]=>int(3) \["c"\]=>int(8) }

\-------------------------------------------------------------------------------

json\_encode() syntax:

json\_encode($variable)

// Encode a variable value to JSON format

e.g.

$age = array("Andy"=>19, "Bob"=>16, "Caddie"=>18);

echo json\_encode($age);

// Output:   {"Andy":19,  "Bob":16,  "Caddie":18}

\-------------------------------------------------------------------------------

key() syntax:

key($array)

// Return the element key of an array according to the current position of the internal pointer. The default position of the key is 0.

e.g.

$arr=array("A","B","C","D");

echo "The key of the current position is: " . key($arr);

// Output:   The key of the current position is: 0

\-------------------------------------------------------------------------------

krsort() syntax:

krsort($array)

// Sorts an associative array keys in descending order

e.g.

$score=array("Rosy"=>"90","Andy"=>"100","Jony"=>"85");

krsort($score);     // sort keys

print\_r($score);

// Output:   Array( \[Rosy\] => 90    \[Jony\] => 85    \[Andy\] => 100 )

\-------------------------------------------------------------------------------

ksort() syntax:

ksort($array)

// Sorts an associative array keys in ascending order.

e.g.

$score=array("Rosy"=>"90","Andy"=>"100","Jony"=>"85");

ksort($score);     // sort keys

print\_r($score);

// Output:   Array( \[Andy\] => 100    \[Jony\] => 85    \[Rosy\] => 90 )

\-------------------------------------------------------------------------------

less / more than syntax:

where FieldName  less/more than value;

// Select records less/more than a specified value in a table.

e.g.

\# 1. Given the current status of the table “books” as follows.

use library;

select \* from books;

![](image_rsrc711.jpg)

\# 2. Show filtered data by using “<=”

select \* from books where price <= 12.00;

![](image_rsrc712.jpg)

// “where price <= 12.00;” shows the price less than or equal to 12.00.

// ( You can try “>=” operator by yourself ).

\-------------------------------------------------------------------------------

limit records syntax:

$sql = "SELECT \* FROM Orders LIMIT records";

// Specify how many records to return.

e.g.

$sql = "SELECT \* FROM Orders LIMIT 50";

// Specify 1- 50 records to return

$sql = "SELECT \* FROM Orders LIMIT 5 OFFSET 10";

// Specify 5 records to return, start from 11

\-------------------------------------------------------------------------------

list() syntax:

list($a, $b, $c, $d, …) = $array;

// Assign multiple values to multiple variables at a time by an array.

e.g.

$arr = array("Ant", "Bee", "Cat", "Dog");

list($a, $b, $c, $d) = $arr;

echo "$a, $b, $c, $d";

// Output:   Ant, Bee, Cat, Dog

\-------------------------------------------------------------------------------

local variable syntax:

function funName(){ $variable=value; }

// A local variable is declared inside the function, it is only used inside current function.

e.g.

<?php  

$num=200;   // This $num is a global variable.

function test( ){

$num=100;   // This $num is a local variable.

echo $num;

}

test();

?>

// Output:   100

\-------------------------------------------------------------------------------

log() syntax:

log(number)

// Return the natural logarithm of a number

e.g.

echo(log(10)." ");   echo(log(1)." ");

// Output:    2.302585092994    0

\-------------------------------------------------------------------------------

ltrim() syntax:

ltrim($string, $substring)

// Remove the spaces or substring from the left side of a string

e.g.

$str = "Hi, Friends";

echo ltrim($str, "Hi,");    // remove Hi,

// Output:   Friends

\-------------------------------------------------------------------------------

mail() syntax:

mail( to, subject, message, headers, parameters);

// Send an email

| to || Specify email recipient. |
| --- | --- |
| subject || Specify email subject |
| message || Specify email content. Separate lines with LF(\\n). |
| headers || (optional) From, Cc, and Bcc. Separate with CRLF(\\r\\n) |
| parameters || (optional) Specify additional parameters for the mail sender. |

// Email content must not exceed 70 characters per line.

e.g.

<?php  
$msg = "email\_text";    // the email contents  
mail("person@demo.com", "subject", $msg);  // send email  
?>

\-------------------------------------------------------------------------------

max() syntax:

max(num1, num2, num3,…);

// Return the largest value among numbers.

e.g.

echo(max(1,3,5,7,9));

// Output:   9

\-------------------------------------------------------------------------------

md5() syntax:

md5($string, bool);

// Generate the MD5 hash of a string. If "bool" is true, generate 16 binary chars, if "bool" is false (default), generate 32 hex chars.

e.g.

$str = "Good";

echo md5($str);    // generate 32 hex characters by default

// Output:   0c6ad70beb3a7e76c3fc7adab7c46acc

\-------------------------------------------------------------------------------

md5\_file() syntax:

md5\_file($file);

// Generate the MD5 hash of a file.

e.g.

$f="myFile.txt";

echo md5\_file($f);

// Output:   2aa71b9b39feee485ace2843c0d0bfbb

\-------------------------------------------------------------------------------

microtime() syntax:

microtime()

// Return the current Unix timestamp with microseconds

e.g.  
echo(microtime());

// Output:   0.51976200 1668780938

\-------------------------------------------------------------------------------

min() syntax:

min(num1, num2, num3,…);

// Return the smallest value among numbers.

e.g.

echo(min(1,3,5,7,9));

// Output:   1

\-------------------------------------------------------------------------------

mkdir() syntax:

mkdir("path/directory/", permission)

// Create a directory with specified permissions, return 1 if successfully.

// About permission, please see Permissions Chart.

e.g.

mkdir("/php/myFolder/", 0770);    // return 0 if fail

// permissions to the owner and the owner's user group

// Output:   1

\-------------------------------------------------------------------------------

mktime() syntax:

mktime($hour, $minute, $second, $month, $day, $year)

// Return a Unix timestamp (seconds) from Unix Epoch (1-1-1970) to the specified date and time. All parameters are optional.

e.g.

<?php  // Return an Unix timestamp from Unix Epoch to current time

print(mktime());  

?>

// Output:   1668797908

\-------------------------------------------------------------------------------

move\_uploaded\_file() syntax:

bool move\_uploaded\_file($file\_tmp\_name, $destination )

// Move an uploaded file with temporary name to new location.

e.g.

move\_uploaded\_file($\_FILES\["file"\]\["tmp\_name"\], "upload/". $\_FILES\["file"\]\["name"\]);

// Move FILES\["file"\]\["tmp\_name"\] to "upload" folder, the new file name becomes $\_FILES\["file"\]\["name"\]).

\-------------------------------------------------------------------------------

mt\_rand() syntax:

mt\_rand(min, max)

// Generate a random number from min to max. Arguments are optional.

e.g.

echo(mt\_rand()."  "); echo(mt\_rand(100,1000));

// Output:   2045534323    168

\-------------------------------------------------------------------------------

mysqli\_affected\_rows() syntax:

mysqli\_affected\_rows()

// Return the number of affected rows from the query.

e.g.

$con=new mysqli("servername","username","password","db");

$sql = "DELETE FROM myTable WHERE id < 6";

mysql\_query($sql, $con);

$rc = mysqli\_affected\_rows();

echo "Records deleted: " . $rc;

mysql\_close($con);

// Records deleted: 5

\-------------------------------------------------------------------------------

mysqli\_close( ) syntax:

mysqli\_close( );

// Close a previously opened database connection

e.g.

$con= mysqli\_connect( "localhost", "root", "12345678" );

mysqli\_close($con);     // close the connection

echo "The connection is closed successfully!";

// Output:

The connection is closed successfully!

\-------------------------------------------------------------------------------

mysqli\_connect() syntax:

mysqli\_connect( "host", "username", "password" );

// "mysqli\_connect( ) lets PHP connect MySql server.

// "host": specifies a host name or an IP address

// "username": specifies a MySql user name.

// "password": specifies a MySql password.

e.g.

$con = mysqli\_connect( "localhost", "root", "12345678" );

if( $con ) {     // if connect MySQL server successfully

echo  " Connect successfully! ";

}

// Output:    Connect successfully!

\-------------------------------------------------------------------------------

mysqli\_connect\_error() syntax:

mysqli\_connect\_error()

// Return the message of the connection error with MySQL

e.g.

$conn = mysqli\_connect("server", "user", "password", "db");

if (!$conn) {

die("Connection failed: " . mysqli\_connect\_error());

}

// Output:   Connection failed: php\_network\_getaddresses: getaddrinfo failed: No such host is known.

\-------------------------------------------------------------------------------

mysqli\_data\_seek() syntax:

mysqli\_data\_seek($result, row);

// Move the pointer to an arbitrary row in the result-set.

// "row" parameter starts from row 0.

e.g.

$con=new mysqli("servername","username","password","db");

$sql="SELECT \* FROM myTable";

if ($result=mysqli\_query($con, $sql)){

mysqli\_data\_seek($result, 5);  // Seek to row 5

}

// Point to row 5 in the result set.

\-------------------------------------------------------------------------------

mysqli\_error() syntax:

mysqli\_error($con);

// Returns the description of the last error.

e.g.

$con=new mysqli("servername","username","password","db");

mysqli\_query($con, "SELECT \* FORM myTable");

$error = mysqli\_error($con);   // Error

print("Error Found: ".$error);

// Output:   Error Found: You have an error in your SQL syntax; ……

\-------------------------------------------------------------------------------

mysqli\_fetch\_array() syntax:

$array=mysqli\_fetch\_array($query)

// "mysqli\_fetch\_array( )" returns an indexed and associative array that contains rows of a table. The element keys can be both number type and string type.  For example: \[number\]=>value    \[string\]=>value.

e.g.

<?php

$con= mysqli\_connect( "localhost", "root", "12345678" );

if( $con ) {     // if connect MySQL server successfully

echo  " Connect successfully! ";

}

$select=mysqli\_select\_db( $con, "myDB" );

if( $select ) {    // if select database "myDB" successfully

echo  " Select myDB successfully!<br> ";

}     // assume that myDB has a table "colortable"

$sql="select \* from colortable";  // "\*" represents all columns

$query=mysqli\_query( $con, $sql);

while ( $array=mysqli\_fetch\_array($query) ){    // return an array

print\_r($array);  // print\_r( ) is used to print the array

echo "<br>";

}

?>

// Output:

Connect successfully!  Select myDB successfully!  
Array (

\[0\] => 1          \[id\] => 1   

\[1\] => red        \[color1\] => red  

\[2\] => yellow     \[color2\] => yellow

\[3\] => green      \[color3\] => green

\[4\] => blue       \[color4\] => blue

\[5\] => sky        \[color5\] => sky

)

\-------------------------------------------------------------------------------

mysqli\_fetch\_assoc() syntax:

$array=mysqli\_fetch\_assoc($query)

// "mysqli\_fetch\_assoc( )" returns an assoc array that contains rows of a table. Its element key is always a string type. e.g. \[string\]=> value.

e.g.

<?php

$con= mysqli\_connect( "localhost", "root", "12345678" );

if( $con ) {     // if connect MySQL server successfully

echo  " Connect successfully! ";

}

$select=mysqli\_select\_db( $con, "myDB" );

if( $select ) {    // if select database "myDB" successfully

echo  " Select myDB successfully!<br> ";

}     // assume that myDB has a table "colortable"

$sql="select \* from colortable";  // "\*" represents all columns

$query=mysqli\_query( $con, $sql);

while ( $array=mysqli\_fetch\_assoc($query) ){    // return an array

print\_r($array);  // print\_r( ) is used to print the array

echo "<br>";

}

?>

// Output:

Connect successfully!  Select myDB successfully!  
Array ( \[id\] => 1   \[color1\] => red   \[color2\] => yellow \[color3\] => green  \[color4\] => blue   \[color5\] => sky )   
Array ( \[id\] => 2   \[color1\] => pink   \[color2\] => navy   \[color3\] => purple   \[color4\] => orange   \[color5\] => olive )

\-------------------------------------------------------------------------------

mysqli\_fetch\_row() syntax:

$array=mysqli\_fetch\_row($query)

// "mysqli\_fetch\_row( )" returns an indexed array that contains rows of a table. Its element key is always a number type.  e.g. \[number\]=> value.

e.g.

<?php

$con= mysqli\_connect( "localhost", "root", "12345678" );

if( $con ) {     // if connect MySQL server successfully

echo  " Connect successfully! ";

}

$select=mysqli\_select\_db( $con, "myDB" );

if( $select ) {    // if select database "myDB" successfully

echo  " Select myDB successfully!<br> ";

}     // assume that myDB has a table "colortable"

$sql="select \* from colortable";  // "\*" represents all columns

$query=mysqli\_query( $con, $sql);

while ( $array=mysqli\_fetch\_row($query) ){    // return an array

print\_r($array);  // print\_r( ) is used to print the array

echo "<br>";

}

?>

// Output:

Connect successfully!  Select myDB successfully!  
Array ( \[0\] => 1  \[1\] => red  \[2\] => yellow  \[3\] => green  \[4\] => blue  \[5\] => sky )   
Array ( \[0\] => 2  \[1\] => pink  \[2\] => navy  \[3\] => purple  \[4\] => orange  \[5\] => olive ) 

\-------------------------------------------------------------------------------

mysqli\_free\_result() syntax:

mysqli\_free\_result($result)

// Release the memory related to the result, return true if succeed.

e.g.

$result = mysqli\_query($con, "SELECT \* FORM myTable");

var\_dump(mysqli\_free\_result($result));

// Output:   bool(true)

\-------------------------------------------------------------------------------

mysqli\_get\_server\_info() syntax:

$version = mysqli\_get\_server\_info($con);

// Return the version of the MySQL server.

e.g.

$con = mysqli\_connect("server", "user", "password", "db");

$version = mysqli\_get\_server\_info($con);

// Output:   MySQL Server Version: 5.7.12-log

\-------------------------------------------------------------------------------

mysqli\_num\_rows() syntax:

$total\_numbers = mysqli\_num\_rows($result);

// Return the number of rows in a result set.

e.g.

$con = mysqli\_connect("server", "user", "password", "db");

$sql="SELECT \*  FROM myTable ";

$result=mysqli\_query($con, $sql) ;

$rowNum=mysqli\_num\_rows($result);

var\_dump($rowNum); // assume that there are 10 records in result

// Output:   int(10)

\-------------------------------------------------------------------------------

mysqli\_query() syntax:

mysqli\_query($queryVariable, $connectVariable);

// Execute the query

e.g.

$con=mysqli\_connect("servername","username","password","db");

if (!$con) {  die('Fail to connect! '); }

$sql = "SELECT \* FROM Mytable";

mysqli\_query($sql, $con);    // run the query

echo "Select data successfully!";

mysqli\_close($con);

// Output:   Select data successfully!

\-------------------------------------------------------------------------------

mysqli\_real\_escape\_string() syntax:

mysqli\_real\_escape\_string($string)

// Escape special characters in a string, making it legal to use in SQL.

e.g.

mysqli\_connect("server", "user", "password", "db");

$sql="SELECT \*  FROM myTable ";

var\_dump( mysql\_real\_escape\_string($sql) );

// Output:   string(25) "SELECT \* FROM \\'myTable\\'"

\-------------------------------------------------------------------------------

mysqli\_result() syntax:

mysqli\_result($result, row, column)

// Return the value in a cell according to the specified row and column in a table.

e.g.

var\_dump( mysql\_result($result, 0, name) );

var\_dump( mysql\_result($result, 1, 'name') );

// Output:  

string(3) "Alf"

string(3) "Bob"

\-------------------------------------------------------------------------------

mysqli\_select\_db() syntax:

mysqli\_select\_db( $con, "databaseName" );

// Select a database to connect a server.

// "$con" is the connection to MySql server. (See mysqli\_connect( )).

// "databaseName" specifies the name of the database.

e.g.

<?php

$con= mysqli\_connect( "localhost", "root", "12345678" );

if( $con ) {     // if connect MySQL server successfully

echo  " Connect successfully! ";

}

$select=mysqli\_select\_db( $con, "myDB" );

if( $select ) {    // if select database "myDB" successfully

echo  " Select myDB successfully!<br> ";

}

?>

// Output:   Connect successfully!  Select myDB successfully!

\-------------------------------------------------------------------------------

namespace syntax:

namespace MyNamespace;

// Namespace can avoid the conflict of two class names, two function names, and two variable names, and two constant names.      

e.g.

namespace MyNameSpace1;        // define the 1st namespace

class MyClass {…}

const DEMO = "Nice!";

function myFun() { … }

namespace MyNameSpace2;     // define the 2nd namespace

class MyClass {…}

const DEMO = "Good!";

function myFun() { … }

// In this example, two class names, two constant names, two function names are the same, however the names of two namespaces are different, therefore, which can resolve the problem of name conflict.

\-------------------------------------------------------------------------------

natcasesort() syntax:

natcasesort($array)

// Sort the array values by using a “natural order” algorithm.

// natcasesort() is case insensitive

e.g.

$arr = array("a26.jpg", "a45.jpg", "A18.jpg", "A32.jpg");

natcasesort($arr);     // case insensitive

print\_r($arr);

// Output:   Array( \[2\] => A18.jpg    \[0\] => a26.jpg    \[1\] => A32.jpg    \[3\] => a45.jpg )

\-------------------------------------------------------------------------------

natsort() syntax:

natsort($array)

// Sort the array values by using a “natural order” algorithm.

// natsort() is case sensitive.

e.g.

$arr = array("a26.jpg", "a45.jpg", "A18.jpg", "A32.jpg");

natsort($arr);     // case sensitive

print\_r($arr);

// Output:   Array( \[2\] => A18.jpg    \[3\] => A32.jpg    \[0\] => a26.jpg    \[1\] => a45.jpg )

\-------------------------------------------------------------------------------

next() syntax:

next($array)

// Return the next element value to which the pointer points.

e.g.

$arr = array("ant", "bee", "cat", "dog");

echo current($arr)." ";    // current element value

echo next($arr);     // next element value

// Output:   ant   bee

\-------------------------------------------------------------------------------

nl2br() syntax:

nl2br("string");

// Insert <br/> where all \\n occur in the string

e.g.

echo nl2br("The first line \\n The second line");

// Output:   The first line <br/>

The second line

\-------------------------------------------------------------------------------

not equal syntax:

where FieldName  !=  value;

// Select some data that is not equal to a specific value.

e.g.

\# 1. Given the current status of the table “books” as follows:

use library;

select \* from books;

![](image_rsrc713.jpg)

\# 2. Show filtered data by using “!\=”

select \* from books where writer != "R.Y.";

![](image_rsrc714.jpg)

// “where writer !\= "R.Y.";” shows the filtered data except the writer who is R. Y.

\-------------------------------------------------------------------------------

null value syntax:

$var = null

// A null value indicates that the variable has no value.

// Null can clear the data of a variable.

e.g.

$var="Hi, my friend!";

$var=null;

var\_dump($var);

// Output:   Null

\-------------------------------------------------------------------------------

number\_format() syntax:

number\_format(number, decimals)

// Format a number with grouped thousands.

e.g.

echo number\_format("8888888", 2);

// Output:   8,888,888.00

\-------------------------------------------------------------------------------

ob\_clean() syntax:

ob\_clean();

// Clean the current contents in the output buffer. Buffer is not closed.

e.g.

ob\_start();   echo "This output will not be seen";

ob\_clean();  

// ob\_clean() stops sending buffer contents to the browser.

\-------------------------------------------------------------------------------

ob\_end\_clean() syntax:

ob\_end\_clean();

// Clean the current contents in the output buffer, then close buffer.

e.g.

ob\_start();   echo "This output will not be seen";

ob\_end\_clean();  

// ob\_end\_clean() stops sending buffer contents to the browser.

\-------------------------------------------------------------------------------

ob\_end\_flush() syntax:

ob\_end\_flush()

// Send the output buffer contents to the browser, then close the buffer.

e.g.

ob\_start();   echo "This output can be seen";

ob\_end\_flush();

// Output:   This output can be seen.

\-------------------------------------------------------------------------------

ob\_flush() syntax:

ob\_flush()

// Send the output buffer contents to the browser. Buffer is not closed.

e.g.

ob\_start();   echo "This output can be seen";

ob\_flush();

// Output:   This output can be seen.

\-------------------------------------------------------------------------------

ob\_get\_clean() syntax:

ob\_get\_clean()

// Store the output buffer contents to a variable, then close the buffer.

e.g.

ob\_start();

echo 'I will be stored in a variable';

$variable = ob\_get\_clean();    // buffer is now closed

echo "Variable value : $variable";

// Output:   Variable value : I will be stored in a variable

\-------------------------------------------------------------------------------

ob\_get\_flush() syntax:

ob\_get\_flush()

// Send the output buffer contents to the browser, and store the output buffer contents to a variable, then close the buffer.

e.g.

ob\_start();

echo "I will be stored in a variable. \\n";

$variable = ob\_get\_flush();    // buffer is now closed

echo "Variable value : $variable";

// Output:   I will be stored in a variable.

Variable value : I will be stored in a variable.

\-------------------------------------------------------------------------------

ob\_get\_contents() syntax:

ob\_get\_contents()

// Send the output buffer contents to the browser, and store the output buffer contents to a variable. The buffer is not closed.

e.g.

ob\_start();

echo "I will be stored in a variable. \\n";

$variable = ob\_get\_contents();    // buffer is not closed

echo "Variable value : $variable";

// Output:   I will be stored in a variable.

Variable value : I will be stored in a variable.

\-------------------------------------------------------------------------------

ob\_get\_length()

ob\_get\_length()

// Get the length of the output buffer contents

e.g.

ob\_start();

echo "R in 8 Hours";     // 12 characters

$length = ob\_get\_length();

echo "\\n"."The length of the output buffer contents: $length ";

// Output:   R in 8 Hours

The length of the output buffer content: 12

\-------------------------------------------------------------------------------

ob\_get\_level() syntax:

ob\_get\_level()

// Return the nesting level of the active output buffers, return 0 if inactive.

e.g.

ob\_start();

$buf\_level = ob\_get\_level();   echo " Buffer level: $buf\_level ";

ob\_start();

$buf\_level = ob\_get\_level();   echo " Buffer level: $buf\_level ";

ob\_start();

$buf\_level = ob\_get\_level();   echo " Buffer level: $buf\_level ";

Output:    Buffer level: 1     Buffer level: 2     Buffer level: 3

\-------------------------------------------------------------------------------

ob\_start() syntax:

ob\_start()

// Start an output buffer, which stores the contents to output.

e.g.

ob\_start();   echo "This output can be seen";

ob\_end\_flush();    // close the buffer

// Output:   This output can be seen

\-------------------------------------------------------------------------------

object syntax:

$object = new class-name;     // create an object

$object\-\>variable;     // an object references a property

$object\-\>functionName( );     // an object references a method

// Object is an instance of a class.

e.g.

<?php

class MyClass{        // define a class

var $p = "A class & object example ";     // define a variable "$p"

}

$obj= new MyClass();    // create an object "obj"

echo $obj \-> p;    // an object references a variable

?>

// Output:   A class & object example

\-------------------------------------------------------------------------------

order by syntax:

SELECT columnName FROM tableName ORDER BY columnName ASC|DESC 

// Sort the records in ascending order or in descending order

e.g.

$sql = "SELECT id, firstname, lastname FROM myTable ORDER BY firstName DESC";

// Sort the firstName in descending order

\-------------------------------------------------------------------------------

overloading syntax:

function \_\_call($name, $arg){…}

// Different object calls a method with same name and with different parameter, which is called overloading.

// \_\_call() can implement method overloading

// \_\_call() is invoked when an inexistent function is called.

// $funName is the function name, $arg is an array parameter.

e.g.

e.g.

<?php

class MyClass {

function \_\_call($name, $arg){    // overloading   

return $arg\[0\] + $arg\[1\];

}}

$obj1 = new MyClass();

echo $obj1\-\>sum(10)." ";      // call \_\_call()

$obj2 = new MyClass();

echo $obj2\-\>sum(20,30)." ";     // call \_\_call()

?>

// Output:   10   50

\-------------------------------------------------------------------------------

override syntax:

class BaseClass{function myFun(){…}}

class DerivedClass extends BaseClass{function myFun(){…}}

// The method of the base class and the method of the derived class owe the same name and same parameter, which is called overriding.

// Overriding means that the method of the derived class overrides the method of the base class.

e.g.

<?php

class Class1{

public function show(){      // the method of the base class

return ' Class1 Information  ';

}}

class Class2 extends Class1{

public function show(){     // the method of the base class

return ' Class2 Message  ';

}}

$obj1 = new Class1();

echo $obj1\-\>show();

$obj2 = new Class2();

echo $obj2\-\>show();

// Output:   Class1 Information      Class2 Message

\-------------------------------------------------------------------------------

parent::\_\_construct() syntax:

parent::\_\_construct();

// In derived class, call the constructor of the base class.

e.g.

<?php

class BaseClass {

function \_\_construct() {

print "I am the constructor of base class" . PHP\_EOL;

}}

class DerivedClass extends BaseClass {

function \_\_construct() {

parent::\_\_construct();  // call the constructor of BaseClass

}}

$obj = new DerivedClass();

?>

// Output:   I am the constructor of base class

\-------------------------------------------------------------------------------

parse\_str() syntax:

parse\_str("string", $array);

// Parse a string to an array

e.g.

parse\_str(" flower=rose & color=red ", $array);

print\_r($array);

// Output:   Array(\[ flower\] => rose    \[color\] => red )

\-------------------------------------------------------------------------------

PHP\_EOL syntax:

echo PHP\_EOL;     // Enter new line

e.g.

echo "Hello world!";

echo PHP\_EOL;    // enter new line

echo "Hi, my friend!";

// Output:

Hello world!

Hi, my friend!

\-------------------------------------------------------------------------------

phpinfo() syntax:

phpinfo();

// Return information about PHP's installation and configuration.

e.g.

phpinfo()

// Output information about PHP version, variables modules, server…

\-------------------------------------------------------------------------------

pi() syntax:

pi();

// Return as approximate value of pi.

e.g.

echo(pi());

//  Output:   3.1415926535898

\-------------------------------------------------------------------------------

polymorphism syntax:

$obj1\-\>myFun();  

$obj2\-\>myFun();

$obj3\-\>myFun();

// Polymorphism refers to that multiple types of objects act on the same name function and obtain different results, which is called polymorphism.

e.g.

<?php

class Work {

function complete(){}

}

class Task1 extends Work  {

function complete() {

print "Task1 has been done.\\n"; 

}}

class Task2 extends Work  {

function complete() {

print "Task2 has been done.\\n"; 

}}

class Task3 extends Work { 

function complete() {

print "Task3 has been done."; 

}}

$obj1=new Task1();  $obj1\-\>complete();

$obj2=new Task2();  $obj2\-\>complete();

$obj3=new Task3();  $obj3\-\>complete();

?>

// Output:

Task1 has been done.

Task2 has been done.

Task3 has been done. 

\-------------------------------------------------------------------------------

pow() syntax:

pow(m, n);

// Return m raised to the power of n.

e.g.

echo(pow(2,3));     echo(pow(-2,4));

// Output:     8     16

\-------------------------------------------------------------------------------

preg\_match() syntax:

preg\_match($pattern, $str);

// Check whether a match was found in a string.

// Return 1 if a match was found, return 0 if not.

e.g.

$str = "PowerShell in 8 Hours";

$pattern = "/shell/i";     // " i " means case insensitive

echo preg\_match($pattern, $str);

// Output:   1

\-------------------------------------------------------------------------------

preg\_match\_all() syntax:

$match\_number = preg\_match\_all($pattern, $string);

// Search for multiple matches in a string by regular expression.

// Return the number of matches in the string

// $pattern: regular expression indicating what to search for.

// $string: the string where the search will be performed.

e.g.

$str = "A cow plows field slowly in the downtown now";

$pattern = "/ow/i";    // find all occurrences of "ow" in a string

$match\_num = preg\_match\_all($pattern, $str);

echo " The 'ow' occurrence number is $match\_num";

// Output:   The 'ow' occurrence number is 6

\-------------------------------------------------------------------------------

preg\_replace() syntax:

preg\_replace(str1, str2, $string)

// Use regular expression to replace the str1 with str2 in a string.

e.g.

$string = 'Scala in 8 Hours';

$pattern = '/scala/i';

echo preg\_replace($pattern, 'Perl', $string);

// Output:   Perl in 8 Hours

\-------------------------------------------------------------------------------

preg\_split() syntax:

preg\_split($pattern, $string)

// Split a string to an array by using a pattern as separators

e.g.

$str = '10-12-2022';

$patt = '/\\D/';    // Split anything which is not a digit

$array = preg\_split($patt, $str);

print\_r($array);

// Output:   Array(\[0\] => 10    \[1\] => 12    \[2\] => 2022)

\-------------------------------------------------------------------------------

prepare() syntax:

prepare("insert into tablename(var1,var2,var3)values(?,?,?)")

prepare("select \* from tablename where var1=? and var2=?")

// Prepare statement is used to execute multiple same SQL statements.

e.g.

<?php

$con=new mysqli("servername","username","password","db");  
$stmt = $con\-\>prepare("INSERT INTO myTable (firstname, lastname, email) VALUES (?, ?, ?)");  
$stmt\-\>bind\_param("sss", $firstname, $lastname, $email); // bind  
// "sss" means 3 strings. If "ids", it means 1 integer, 1 double, 1 string.

$firstname = "Ray";     $lastname = "Yao";  
$email = "xxx@yyy.com";  
$stmt\-\>execute();    // run  
echo "Insert data successfully";  
?>

// Output:   Insert data successfully

\------------------------------------------------------------------------------

prev() syntax:

prev($array)

// Return the previous element in the array

e.g.

$a = array("A ", "B ", "C ");

echo current($a);  echo next($a);  echo prev($a);

// Output:   A  B  A

\-------------------------------------------------------------------------------

print syntax:

print "content";    

print ("content");

// Output string or value of a variable.

e.g.

print " Hello World! ";

print (" Hello World! ");

// Output:   Hello World!   Hello World!

// The different between "echo" and "print":

// "echo" can output one or more strings, without return value.

// "print" only outputs one string and can return a value 1.

\-------------------------------------------------------------------------------

printf() syntax:

printf(" %format", $variable);

// Print a format string.

// Replace the %format with the value of $variable

// About %format, please see The String Format Chart.

e.g.

$num = 8;   $str = "Hours";

printf("JAVA in %u %s.", $num, $str);

// $num replaces %u, $str replaces %s

// Output:   JAVA in 8 Hours

\-------------------------------------------------------------------------------

print\_r() syntax:

print\_r($variable);

// Print or show information stored in a variable

e.g.

$var = array("A", "B", "C");

print\_r($var);

// Output:   Array ( \[0\] => A   \[1\] => B   \[2\] => C )

\-------------------------------------------------------------------------------

private syntax:

private $variable=value;

private function $funName(){}

// The private variable and the private function are only accessed by the current class.

e.g.

<?php

class ParentClass{

private $a=30;  private $b=20;

function add()  {

echo $this\-\>a + $this\-\>b."  ";      // can access private variable

}}    

class ChildClass extends ParentClass{ 

function sub(){

echo $this\-\>a - $this\-\>b."  ";     // cannot access private variable

}}    

$obj= new ChildClass;

$obj\-\>add();

$obj\-\>sub();

?>

// Output:     50     0

// PHP Warning:  Undefined property: ChildClass::$a in line 9

// PHP Warning:  Undefined property: ChildClass::$b in line 9

\-------------------------------------------------------------------------------

protected syntax:

protected $variable=value;

protected function $funName(){}

// The protected variable and the protected function are only accessed by the current class, the base class and the derived class.

// Without the relationship of base class and derived class, the protected member cannot be accessed.

e.g.

<?php

class ParentClass{

protected $a=30;  protected $b=20;

function add()  {

echo $this\-\>a + $this\-\>b."  ";      // can access protected variable

}}    

class ChildClass extends ParentClass{ 

function sub(){

echo $this\-\>a - $this\-\>b."  ";       // can access protected variable

}}    

$obj= new ChildClass;

$obj\-\>add();

$obj\-\>sub();

?>

// Output:     50     10

\-------------------------------------------------------------------------------

public syntax:

public $variable=value;

public function $funName(){}

// The public variable and the public function can be accessed by the current class, the base class and the derived class.

e.g.

<?php

class ParentClass{

public $a=30;  public $b=20;

function add()  {

echo $this\-\>a + $this\-\>b."  ";      // can access public variable

}}    

class ChildClass extends ParentClass{ 

function sub(){

echo $this\-\>a - $this\-\>b."  ";       // can access public variable

}}    

$obj= new ChildClass;

$obj\-\>add();

$obj\-\>sub();

?>

// Output:     50     10

\-------------------------------------------------------------------------------

putenv() syntax:

putenv("VARIABLE=value");

// Set an environment variable and a value.

e.g.

putenv("USER=Ray Yao");

echo "The user name is: " . getenv("USER");

// Output:   The user name is: Ray Yao

\-------------------------------------------------------------------------------

query() syntax:

connectVariable \-\> query(queryVariable)

// Execute the query

e.g.

<?php

$con=new mysqli("servername","username","password","db");

if(!$con\-\>connect\_errno){    // check connection

$sql = "INSERT INTO myTable(name, age, email)

VALUES (\\"Ray Yao\\", \\"28\\", \\"xxx@yyy.com\\")";  

if( $con\-\>query($sql) ){    // $con\-\>query($sql) runs query

echo "Data inserted successfully.";

}}

$con\-\>close();

?>

// Output:   Data inserted successfully

\-------------------------------------------------------------------------------

radio button syntax:

<input type="radio"  name="data" value="myValue">

// type="radio" is used to input data by single choice.

// name="data" specifies the inputted data that will be passed to the PHP file for processing.

// value="myValue" specifies one of the optional contents.

e.g.

<?php

$data = isset($\_GET\['data'\])? htmlentities($\_GET\['data'\]) : "";

if($data) {

if($data =='Matlab') { echo 'Matlab in 8 Hours';}

else if($data =='Kotlin') { echo 'Kotlin in 8 Hours'; }

else if($data =='Pandas') { echo 'Pandas in 8 Hours'; }

} else {

?><form action="" method="get">

<input type="radio" name="data" value="Matlab" />Matlab

<input type="radio" name="data" value="Kotlin" />Kotlin

<input type="radio" name="data" value="Pandas" />Pandas

<input type="submit" value="Submit">

</form>

<?php

}

?>

// Output:

![](image_rsrc715.jpg)

Kotlin in 8 Hours

\-------------------------------------------------------------------------------

rand() syntax:

rand(min, max)

// Generate an integer from min to max

e.g.  
echo(rand(100,1000));

// Output:    268

\-------------------------------------------------------------------------------

readfile() syntax:

readfile("filename", bool);

// Read a file. Set "bool" to true if search for the file in include\_path.

e.g.  
echo readfile("myFile.txt");    // myFile.txt contains "Hello World!"

// Output:   Hello World!

\-------------------------------------------------------------------------------

remove database syntax:

drop database if exists DatabaseName;

// Remove a database in mysql server.

e.g.

drop database if exists garage;

// “drop database if exists garage;” removes a database named “garage” if this database exists currently.

\-------------------------------------------------------------------------------

remove table syntax:

drop table if exists TableName;

// Remove a table in the current database

e.g.

drop table if exists myTable;

// “drop table if exists myTable;” removes a table named “myTable” if this table exists currently.

\-------------------------------------------------------------------------------

rename() syntax:

rename(oldfile, newfile);

// Move and rename oldfile to newfile.

e.g.

rename("/dir1/file1.txt","/dir2/file2.txt");

// Move /dir1/file1.txt to the /dir2/file2.txt, and rename file1.txt to file2.txt

\-------------------------------------------------------------------------------

require() syntax:

require( "anotherFile.php" )    

// Import the code from another.php to the current file

// require() is usually in the top of the file. If the program has an error, the program will stop running.

e.g.

1.   <!—file1.php\-\->

<?php   echo " From file1.php ";  ?>

2.   <!\-\-file2.php\-\->

<?php  

require("file1.php");    // import file1.php to here

echo " From file2.php ";

?>     <!\-\-run file2.php\-\->

// Output:     From file1.php     From file2.php

\-------------------------------------------------------------------------------

require\_once() syntax:

require\_once( "anotherFile.php" )    

// Import the code from another.php to the current file for only once.

// require\_once() is usually in the top of the file. If the program has an error, the program will stop running.

e.g.

1.   <!—file1.php\-\->

<?php   echo " From file1.php ";  ?>

2.   <!\-\-file2.php\-\->

<?php  

require\_once("file1.php");    // import file1.php to here once

echo " From file2.php ";

?>

// Output:     From file1.php     From file2.php

\-------------------------------------------------------------------------------

reset form syntax:

<input type="reset"  value="xxx">

// Reset all data in the form.

// "value" attribute sets the characters on the button.

e.g.

<form action="myfile.php"  method="post">

<input type="reset"  value="RESET">

</form>

// Output:

| RESET |
| --- |

\-------------------------------------------------------------------------------

reset() syntax:

reset($array)

// Return the first element of an array.

e.g.

$arr = array("ant", "bee", "cat", "dog");

echo reset($arr);

// Output:   ant

\-------------------------------------------------------------------------------

return syntax:

return  value;

// "return value" is used to return a value to the function caller.

e.g.

function multiply($x, $y){

return $x \* $y;   // return the value to the function caller

}

echo( multiply(10,20));    // this is a function caller

// Output:   200

\------------------------------------------------------------------------------

rmdir() syntax:

rmdir(/directory);

// Remove the empty directory.

e.g.

rmdir('/temp/mydir');    // mydir is an empty directory

// Remove the directory /temp/mydir

\------------------------------------------------------------------------------

round() syntax:

round($float, decimal\_places);

// Round up the $float according to the number of decimal places.

e.g.

var\_dump(round(3.1415926535898, 3));

// Output:   3.142

\-------------------------------------------------------------------------------

rsort() syntax:

rsort($array)

// Sort the array element values in descending order

e.g.

$arr=array("30","10","20");

rsort($arr);      // sort element values

print\_r($arr);

// Output:   Array(\[0\] => 30    \[1\] => 20    \[2\] => 10)

\-------------------------------------------------------------------------------

rtrim() syntax:

rtrim($string, $substring)

// Remove the spaces or substring from the right side of a string

e.g.

$str = "Hi, Friends";

echo rtrim($str, "Friends");    // remove Friends

// Output:   Hi,

\-------------------------------------------------------------------------------

scandir() syntax:

scandir("/directory");

// Return all sub directories and files inside the specified directory.

e.g.

$array = scandir(''/directory");

print\_r($array);    // result vary

// Output:   Array(\[0\]=>.  \[1\]=>..  \[2\]=>subDir  \[3\]=>f1.php  \[4\]=>f2.txt)

\-------------------------------------------------------------------------------

select data syntax:

SELECT columnName FROM tableName

SELECT \* FROM tableName

// Select data from one or more tables. "\*" means all columns

e.g.

<?php  
$con=new mysqli("servername","username","password","db");  
$sql = "SELECT id, firstname, lastname FROM myTable";  
$result = $con\-\>query($sql);    // execute the query  
if ($result\-\>num\_rows > 0) {      
while($row = $result\-\>fetch\_assoc()) {  
echo "ID: ". $row\["id"\]. " First Name: ". $row\["firstname"\]. "Last Name: ". $row\["lastname"\]. PHP\_EOL;   // show data in each row  
}} else {  
  echo "0 results";  
}

?>

// num\_rows() returns how many rows of the table

// fetch\_assoc() returns an assoc array that contains rows of a table. Its key is always a string type. For example: \[ string \]=> value.

\-------------------------------------------------------------------------------

select data syntax:

$sql="select column from table-name";

$query=mysqli\_query($con, $sql);

// $sql="select column from table-name" is used to retrieve table data by the column name from a table.

// $query=mysqli\_query($con, $sql) executes the query.

// "$con" is the connection to MySql server. (See previous page).

e.g.

<?php

$con= mysqli\_connect( "localhost", "root", "12345678" );

if( $con ) {     // if connect MySQL server successfully

echo  " Connect successfully! ";

}

$select=mysqli\_select\_db( $con, "myDB" );

if( $select ) {    // if select database "myDB" successfully

echo  " Select myDB successfully!<br> ";

}     // assume that myDB has a table "colortable"

$sql="select id, color1 from colortable";

// select two columns "id" and "color1" in the table "colortable"

$query=mysqli\_query( $con,$sql );   // run query

if( $query ) {

echo  " Retrieve data successfully! <br>";

}

while($row = mysqli\_fetch\_array($query)){   // return an array

echo("<br> ID: ".$row\["id"\]);  // show $row\["id"\] value

echo("<br> color1: ".$row\["color1"\]);   // show $row\["color1"\] value

}    

?>

// Output:

Connect successfully!  Select myDB successfully!  
Retrieve data successfully! 

\-------------------------------------------------------------------------------

select to show table syntax:

select  \*  from TableName;

// Show and view all data in a table of a database.

e.g.

use library;

select \* from books;

![](image_rsrc716.jpg)

// “select \* from books;” shows all data in the table “books”.

// There are 3 records and 4 fields in the table “books” of the "library".

\-------------------------------------------------------------------------------

select option syntax:

<select name="data", id="xx" multiple size = number>

<option value="">Please select one item</option>

<option value="value1">text1</option>

<option value="value2">text2</option>

<option value="value3">text3</option>

</select>

// Get the value of the drop-down menu by the name property of the select. If it is multiple selection, please use "multiple size='number'".

e.g.

<?php

$data = isset($\_GET\['data'\])? htmlentities($\_GET\['data'\]) : "";

if($data) {    // get the data value from the form

if($data =='MATLAB') { echo 'Matlab in 8 Hours'; }

else if($data =='KOTLIN') { echo 'Kotlin in 8 Hours'; }

else if($data =='PANDAS') { echo 'Pandas in 8 Hours'; }

} else {

?>

<form action="" method="get">

<select name="data">

<option value="">Please select one book</option>

<option value="MATLAB">Matlab</option>

<option value="KOTLIN">Kotlin</option>

<option value="PANDAS">Pandas</option>

</select>

<input type="submit" value="Submit">

</form>

<?php

}

?>

// Output:  

![](image_rsrc717.jpg)

Kotlin in 8 Hours

\-------------------------------------------------------------------------------

serialize() syntax:

serialize(values);

// Create a storable representation of values.

e.g.

$var = serialize(array("ant", "bee", "cat", "dog"));

echo $var;

// Output:   a:4:{i:0;s:3:"ant";i:1;s:3:"bee";i:2;s:3:"cat";i:3;s:3:"dog";}

\-------------------------------------------------------------------------------

session\_destroy() syntax:

session\_destroy();

// Destroy all of the data related to the current session.

e.g.

session\_start();

$\_SESSION\["color"\]="red";

session\_destroy();

echo "Session has been destroyed ";

// Output:   Session has been destroyed

\-------------------------------------------------------------------------------

session\_id()syntax:

<?php session\_start()?>     // start a session

<a href = "anotherPage.php<?php echo(SID);?>">…</a>

// pass the session id to another page

<?php echo(session\_id());?>     // show session id

e.g.

1.   <!\-- aFile.php -\->

<?php session\_start()?>   <!\-\-  start php session \-\->

<br>Here is "First Page".<br>

<br>Send out a session id to the second page<br><br>

<a href = "bFile.php<?php echo(SID);?>">To Second Page</a>  

<!\-\- pass session id to the bFile.php \-\->

<!\-\- save this file with the name "aFile.php" in the working folder\-\-\> 

2.   <!\-\- bFile.php -\->

<?php session\_start()?>  <!\-\- start php session \-\->

<br>Here is "Second Page".<br>

<br>The session id is: <br><br>

<?php echo(session\_id());?>   <!\-\- show session id \-\->

<!\-\- save the file with the name "bFile.php" in the working folder\-\-\> 

<!\-\- please run the aFile.php \-\-\>  

// Output:

Here is "First Page".  
Send out a session id to the second page  
[To Second Page](http://localhost/B.php)

// Output:

Here is "Second Page".  
The session id is:   
m4tiga6576moc23dma5jugt8cm

\-------------------------------------------------------------------------------

session\_name() syntax:

session\_name("name")     // set a session name

session\_name()     // get the session name

e.g.

session\_name('mySession');     // set a session name

session\_start();

echo session\_name();     // get the session name

// Output:   mySession

\-------------------------------------------------------------------------------

session\_regenerate\_id() syntax:

session\_regenerate\_id();

// Create a new session id, without losing any current session information except the session id.

e.g.

session\_start();

echo session\_id()."\\n";

session\_regenerate\_id();     

echo session\_id();

// Output:   a5d7850ff6afa6135b17e6dd69ec0a22

b6p9861rf8bib7057a32v8ap36gd7b68

\-------------------------------------------------------------------------------

session\_start() syntax:

<?php session\_start()?>     // start a session

<a href = "anotherPage.php<?php echo(SID);?>">…</a>

// pass the session id to another page

<?php echo(session\_id());?>     // show session id

e.g.

1.   <!\-- aFile.php -\->

<?php session\_start()?>   <!\-\-  start php session \-\->

<br>Here is "First Page".<br>

<br>Send out a session id to the second page<br><br>

<a href = "bFile.php<?php echo(SID);?>">To Second Page</a>  

<!\-\- pass session id to the bFile.php \-\->

<!\-\- save this file with the name "aFile.php" in the working folder\-\-\> 

2.   <!\-\- bFile.php -\->

<?php session\_start()?>  <!\-\- start php session \-\->

<br>Here is "Second Page".<br>

<br>The session id is: <br><br>

<?php echo(session\_id());?>   <!\-\- show session id \-\->

<!\-\- save the file with the name "bFile.php" in the working folder\-\-\> 

<!\-\- please run the aFile.php -\-\>  

// Output:

Here is "First Page".  
Send out a session id to the second page  
[To Second Page](http://localhost/B.php)

// Output:

Here is "Second Page".  
The session id is:   
m4tiga6576moc23dma5jugt8cm

\-------------------------------------------------------------------------------

session\_status() syntax:

session\_status()   // Return the session status 0, 1, 2

0 – PHP\_SESSION\_DISABLED:  Sessions are currently disabled.

1 – PHP\_SESSION\_NONE:  No session has been started.

2 – PHP\_SESSION\_ACTIVE:  A session has been started.

e.g.

session\_start();  

$sta = session\_status();

echo ("Current session status is: ".$sta);

// Output:   Current session status is: 2

\-------------------------------------------------------------------------------

session\_unset() syntax:

session\_unset();

// Release all session variables

e.g.

session\_start();

$\_SESSION\['flower'\] = 'Rose';

echo $\_SESSION\['flower'\];

session\_unset();

echo $\_SESSION\['flower'\];   // session variable has been released

// Output:   Rose

// PHP Warning:  Undefined array key "flower" on line 6

\-------------------------------------------------------------------------------

session\_write\_close() syntax:

session\_write\_close();

// Save the session data and end the current session.

e.g.

session\_start();

session\_write\_close();

// Output:   Returns true if succeeds, return false if fails

\-------------------------------------------------------------------------------

set\_error\_handler() syntax:

set\_error\_handler("myErrorHandler")

// Set a user-defined error handler

"myErrorHandler(myHandler($errno, $errmsg, $errfile, $errline){…}

// A user-defined function for handling the error.

e.g.

<?php

function myHandler($errno, $errmsg, $errfile, $errline){

echo " Error No:\[$errno\].  Error Message:$errmsg. ";

echo " Error Line:$errline.  Error File:$errfile. ";

}

set\_error\_handler("myHandler");   // user-defined error handler

$var = -100;

if ($var<0) { trigger\_error("A custom error triggered");}

?>

// Output:

Error No:\[1024\].  Error Message:A custom error triggered.  Error Line:8.  Error File:/server/script.php.

\-------------------------------------------------------------------------------

set\_exception\_handler() syntax:

set\_exception\_handler("handlerFunction");

// Set a user-defined exception handler function.

e.g.

<?php

function myHandler($e){    // handler function

echo $e\-\>getMessage();

}

set\_exception\_handler("myHandler");

throw new Exception("An exception occurs!");

?>

// Output:   An exception occurs!

\-------------------------------------------------------------------------------

setcookie() syntax:

setcookie( "name",  "value" );  // set cookie name and value

$\_COOKIE\["name"\];  // get cookie value by cookie name

e.g.

1.    // in aFile.php

<?php  

setcookie("color", "blue");   // set a cookie

// cookie name is "color", cookie value is "blue"

header("location: bFile.php");      // redirect to bFile.php

?>

<!\-\-save this file with the name "aFile.php" in the working folder\-\->

2.    // in bFile.php

<?php  

$mycolor = $\_COOKIE\["color"\];  // get the cookie from aFile.php

// get the cookie whose name is "color"

echo  $mycolor;    // show the color's value

?>

<!\-\-save the file with the name "bFile.php" in the working folder\-\->

<!\-\-please run the aFile.php\-\-\> 

// Output:     blue

\-------------------------------------------------------------------------------

sha1() syntax:

sha1(string)

// Perform a sha1 hash encryption on a string.

e.g.

echo sha1("Hello");

// Output:   f7ff9e8b7bb2e09b70935a5d785e0cc5d9d0abf0

\-------------------------------------------------------------------------------

sha1\_file() syntax:

sha1\_file(file)

// Perform a sha1 hash encryption on a file.

e.g.

echo sha1\_file("myFile.txt");

// Output:   acg1r62dpcv8s9h5brwus0cq23kdz67g92b3gsb8

\-------------------------------------------------------------------------------

show databases syntax:

show databases;

// View all the available databases in the current mysql server.

e.g.

mysql > show databases;

![](image_rsrc718.jpg)

\------------------------------------------------------------------------------

show specified field syntax:

select field1, field2, field3 from TableName;

// show some specified fields in a table

e.g.

\# 1. Given the current status of the table “books” as follows:

use library;

select \* from books;

![](image_rsrc719.jpg)

\# 2. Show some specified fields

use library;

select title, price from books;

![](image_rsrc71A.jpg)

// “select title, price from books;” only shows two fields “title, price” in the table “books”.

\-------------------------------------------------------------------------------

show specified record syntax:

select \* from TableName where field = value;

// Show a specified record in a table.

e.g.

\# 1. Given the current status of the table “books” as follows:

use library;

select \* from books;

![](image_rsrc71B.jpg)

\# 2. Add a record, and then show this record

use library;

insert into books (id, title, writer, pages, price, publish)

values (7, "Lamp", "Jan Poe",120, 11.67, 2015);

select \* from books where writer = "Jan Poe";

![](image_rsrc71C.jpg)

// “select \* from books where writer = "Jan Poe";” only shows the record where writer is Jan Poe.

\-------------------------------------------------------------------------------

show tables syntax:

show tables;

// Show all existing tables in the current database.

e.g.

mysql> use world;

Database changed

mysql> show tables;

![](image_rsrc71D.jpg)

// “use world;” specifies to use a database “world”.

// “show tables” displays all tables in the database “world”.

// There are three tables totally in the database “world”.

\-------------------------------------------------------------------------------

shuffle() syntax:

shuffle($array)

// Shuffle the order of array elements at random.

e.g.

$arr = array("a", "b", "c", "d");

shuffle($arr);   

print\_r($arr);

// Output:   Array(\[0\] => c    \[1\] => b    \[2\] => d    \[3\] => a)

\-------------------------------------------------------------------------------

simplexml\_load\_file() syntax:

$xml = simplexml\_load\_file("myFile.xml")

$xml \-\> node

// Get data from a xml file, and print out contents according to nodes

e.g.

1. Assume that the content of myFile.xml is:

<?xml version='1.0' encoding='UTF-8'?>

<note>

<from>Ray Yao</from>

<greeting>Hi, My friend!</greeting>

</note>

2.

<?php  
$xml=simplexml\_load\_file("myFile.xml") or die("Error!");  
echo $xml\-\>from."<br>";  
echo $xml\-\>greeting."<br>";  
?>

// Output:     Ray Yao     Hi, My friend!

\-------------------------------------------------------------------------------

simplexml\_load\_string() syntax:

simplexml\_load\_string(myXmlData)

// Get XML data of a string and print them out.

e.g.

<?php

$myXML="<?xml version='1.0' encoding='UTF-8'?>

<note>

<from>Ray Yao</from>

<greeting>Hi, My friend!</greeting>

</note>";

$xml=simplexml\_load\_string($myXML) or die("Error!");

print\_r($xml);

?>

// Output:  

SimpleXMLElement Object(

\[from\] => Ray Yao

\[greeting\] => Hi, My friend!

)

\-------------------------------------------------------------------------------

sleep() syntax:

sleep(seconds)

// Delay running the current code for a specified seconds

e.g.

sleep(3);

// Pause for 3 seconds before continuing.

\-------------------------------------------------------------------------------

sort() syntax:

sort($array)

// Sort the array element values in ascending order

e.g.

$arr=array("30","10","20");

sort($arr);      // sort element values

print\_r($arr);

// Output:   Array( \[0\] => 10    \[1\] => 20    \[2\] => 30 )

\-------------------------------------------------------------------------------

sort table data syntax:

order by field asc / desc;

// Sort data in ascending order by using "asc" keyword.

// Sort data in descending order by using "desc" keyword.

e.g.

\# 1. Given the current status of the table “books” as follows:

use library;

select \* from books;

![](image_rsrc71E.jpg)

\# 2. Sort the table by using “asc”

use library;

select \* from books order by price asc;

![](image_rsrc71F.jpg)

// “select \* from books order by price asc;” sorts the “price” data in ascending order.

\-------------------------------------------------------------------------------

sprintf() syntax:

$variable = sprintf("%format", $variable);

// Write a formatted string to a new variable

// Replace the %format with the value of $variable

// About %format, please see The String Format Chart.

e.g.

$num = 8;   $str = "Hours";

$var = sprintf("JAVA in %u %s.", $num, $str);

// $num replaces %u, $str replaces %s

echo $var;

// Output:   JAVA in 8 Hours

\-------------------------------------------------------------------------------

sqrt() syntax:

sqrt(number):

// Return a square root of a number

e.g.

echo(sqrt(25).' ');  echo(sqrt(0.81).' ');

// Output:       5       0.9

\-------------------------------------------------------------------------------

sscanf() syntax:

sscanf($string, "%format");

// Parse a string according to the specified format.

// About %format, please see The String Format Chart.

e.g.

$str = "Java in 8 Hours";

$format = sscanf($str,"%s %s %d %s");

print\_r($format);

// Output:   Array(\[0\] => Java    \[1\] => in    \[2\] => 8    \[3\] => Hours)

\-------------------------------------------------------------------------------

static syntax:

static $variable = value;

// Static variable can retain the value from the last time the function was called.

e.g.

<?php function myFun() {

static $var=10;   

echo $var++;    // $var value will keep to next function call

echo "  ";     

}

myFun();  myFun();  myFun();

?>

// Output:   10   11   12

\-------------------------------------------------------------------------------

static member syntax:

static $variable = value;

static function funName(){…}

ClassName::$variable     // the class references the variable

ClassName::funName()     // the class references the function

// The static member can be directly called by a class, not by an object.

e.g.

<?php

class MyClass {

public static $staticVar = 'I am a static variable';

public static function staticFun(){

echo "I am a static function";

}}

print MyClass::$staticVar . PHP\_EOL;     // called by a class

print MyClass::staticFun() . PHP\_EOL;    // called by a class

?>

// Output:

I am a static variable

I am a static function

\-------------------------------------------------------------------------------

string syntax:

$str = "characters";

$str = 'characters';

// String consist of a sires of characters, which are enclosed by double quotes or single quotes usually.

e.g.

$x = " Hello world! ";

echo $x;

$y = ' Hi, my friend! ';

echo $y;

// Output:   Hello world!  Hi, my friend!

\-------------------------------------------------------------------------------

string connecting syntax:

$string1 . " " . $string2

// Connect two strings

e.g.

$book1 = "PowerShell";

$book2 = "in 8 Hours";

echo $book1 . " " . $book2;

// Output:   PowerShell in 8 Hours

\-------------------------------------------------------------------------------

stripos() syntax:

stripos(string, substring)

// Return the position of the first occurrence of the substring in string.

// stripos() is case insensitive.

e.g.

echo stripos("Powershell & Shell Scripting in 8 Hours", "Shell");

// Output:   5

\-------------------------------------------------------------------------------

stripslashes() syntax:

stripslashes("backslashes")

// Remove backslashes \\ and \\\\.

e.g.

echo stripslashes("I don\\'t know!");

// Output:   I don't know!

\-------------------------------------------------------------------------------

stristr() syntax:

stristr("string", "substring")

// Search for the first occurrence of a substring and return the rest part.

e.g.

echo stristr("Hi, My friends!", "my");    // stristr() is case insensitive

// Output:   My Friends!

\-------------------------------------------------------------------------------

strip\_tags() syntax:

strip\_tags("string\_with\_html\_tags");

// Remove any html tags from a string.

e.g.

echo strip\_tags("The book is <b><i>'R in 8 Hours'</i></b>");

// Output:   The book is 'R in 8 Hours'

\-------------------------------------------------------------------------------

str\_ireplace() syntax:

str\_ireplace(old\_str, "new\_str", "original\_str")

// In the original string, replace a old string with a new string.

e.g.

// str\_ireplace() is case insensitive

echo str\_ireplace("JQuery", "MySQL", "jQuery in 8 Hours");

// Output:   MySQL in 8 Hours

\-------------------------------------------------------------------------------

strlen( ) syntax:

strlen($string);

// Return a length of a string and space

e.g.

$string="  Hello World!  ";

echo strlen( $string );   // return string length

// Output:   16

\-------------------------------------------------------------------------------

str\_pad() syntax:

str\_pad(string, length, pad)

// Pad a string to a specified length

e.g.

$str = "So Good";

echo str\_pad($str,10,"$");   // pad by "$" to the length as 10

// Output:   So Good$$$

\-------------------------------------------------------------------------------

strpbrk() syntax:

strpbrk("string", "character")

// Search a string for the specified character that is the first occurrence and return the rest substring.

e.g.

echo strpbrk("NumPy in 8 Hours", "i");   // strpbrk() is case sensitive

// Output:   in 8 Hours

\-------------------------------------------------------------------------------

strpos() syntax:

strpos(string, substring)

// Return the position of the first occurrence of the substring in string.

// strpos() is case sensitive.

e.g.

echo strpos("Powershell & Shell Scripting in 8 Hours", "Shell");

// Output:   13

\-------------------------------------------------------------------------------

str\_repeat() syntax:

str\_repeat(string, repeat\_number)

// Repeat a string according to the specified number of times

e.g.

echo str\_repeat("Good! ", 3);     // repeat 3 times

// Output:   Good! Good! Good!

\-------------------------------------------------------------------------------

strrev() syntax:

strrev("string")

// Reverse a string

e.g.

echo strrev("abcde");

// Output:   edcba

\-------------------------------------------------------------------------------

strripos() syntax:

strripos(string, substring)

// Return the position of the last occurrence of the substring in string.

// strripos() is case insensitive.

e.g.

echo strripos("Powershell & Shell Scripting in 8 Hours", "shell");

// Output:   13

\-------------------------------------------------------------------------------

strrpos() syntax:

strrpos(string, substring)

// Return the position of the last occurrence of the substring in string.

// strrpos() is case sensitive.

e.g.

echo strrpos("Powershell & Shell Scripting in 8 Hours", "shell");

// Output:   5

\-------------------------------------------------------------------------------

strstr() syntax:

strstr("string", "substring")

// Search for the first occurrence of a substring and return the rest part.

e.g.

echo strstr("Hi, My friends!", "My");    // strstr() is case sensitive

// Output:   My Friends!

\-------------------------------------------------------------------------------

strtolower( ) syntax:

strtolower($string);

// Return a lowercase string

e.g.

$string="  Hello World!  ";

echo strtolower($string);   // return lowercase

// Output:   hello world!

\-------------------------------------------------------------------------------

strtotime() syntax:

strtotime()

// Return the number of seconds since January 1 1970 00:00:00 GMT

e.g.

echo(strtotime("now")." ");

echo(strtotime("next Friday")." ");

echo(strtotime("last Monday")." ");

// Output:     1667875862     1668124800     1667779200  

\-------------------------------------------------------------------------------

strtoupper() syntax:

strtoupper($string);

// Return a uppercase string

e.g.

$string="  Hello World!  ";

echo strtoupper($string);   // return uppercase

// Output:   HELLO WORLD!

\-------------------------------------------------------------------------------

str\_replace() syntax:

str\_replace(old\_str, "new\_str", "original\_str")

// In the original string, replace a old string with a new string.

e.g.

// str\_replace() is case sensitive

echo str\_replace("Rust", "Perl", "Rust in 8 Hours");

// Output:   Perl in 8 Hours

\-------------------------------------------------------------------------------

str\_shuffle() syntax:

str\_shuffle("string")

// Shuffle all characters of a string at random.

e.g.

echo str\_shuffle("abcde");

// Output:   bdaec

\-------------------------------------------------------------------------------

str\_split() syntax:

str\_split("string")

// Split a string to an array

e.g.

print\_r(str\_split("html"));

// Output:   Array(\[0\] => h    \[1\] => t    \[2\] => m    \[3\] => l)

\-------------------------------------------------------------------------------

str\_word\_count() syntax:

str\_word\_count("string")

// Count the words in a string. ( except count the digit. )

e.g.

echo str\_word\_count("Hi, My friends!");     // 3 words

// Output:   3

\-------------------------------------------------------------------------------

strtr() syntax:

$array = array(key=>value);     // the value will replace the key

strtr( "string", $array);    // all values of array replace the string

// Replace the string with an array values

e.g.

$arr = array("Hi," => "Hello,", "Friends" => "World");

echo strtr("Hi, Friends", $arr);  // "Hello, World" replaces "Hi, Friends"

// Output:   Hello, World

\-------------------------------------------------------------------------------

submit form syntax:

<input type="submit"  value="xxx">

// Submit all data in the form to the server.

// "value" attribute sets the characters on the button.

e.g.

<form action="myfile.php"  method="post">

<input type="submit"  value="SUBMIT">

</form>

// Output:

| SUBMIT |
| --- |

\-------------------------------------------------------------------------------

substr() syntax:

substr(string, start, length)

// Extract a substring by the specified parameters

// "start" specifies the index where to start to extract

// "length" specified the length to extract

e.g.

echo substr("JavaScript in 8 Hours!",4,6);

// Output:   Script

\-------------------------------------------------------------------------------

substr\_count() syntax:

substr\_count("string", "word")

// Count how many the specified word occurs in a string.

e.g.

echo substr\_count("OK! It is OK!", "OK");    // count "OK"

// Output:   2

\-------------------------------------------------------------------------------

substr\_replace() syntax:

substr\_replace(string, new, start)

// Replace part of string with new string from the specified position

// "start" specified a position where the replacement occurs.

e.g.

echo substr\_replace("12345678", "OK", 3);

// Output:   123OK

\-------------------------------------------------------------------------------

switch syntax:

switch ( $variable ) {

case 1: // if equals this case, do this;  break;

case 2: // if equals this case, do this;  break;

case 3: // if equals this case, do this;  break;

default : // if not equals any case, run default code;  break;

}

// $variable value will compare each case first, if it equals one of the "case" value; it will run that "case" code. Otherwise, run default code.

e.g.

$number=20;

switch ( $number ) {  // $number will compare each case

case 10 : echo "Running case 10";  break;

case 20 : echo "Running case 20";  break;    // match

case 30 : echo "Running case 30";  break;

default :  echo "Running default code";  break;  }

// Output:   Running case 20

\-------------------------------------------------------------------------------

text input syntax:

<input type="text"  name="data">

// input type="text" specifies the input type is "text",

// name="data" specifies the inputted "data" that will be passed to the PHP file for processing.

e.g.

<html>

<form action=" " method="post">

Name: <input type="text" name="myName">

<input type="submit" value="Submit">

</form>

<?php echo $\_POST\["myName"\]; ?><br>

</html>

// Output:

![](image_rsrc70R.jpg)

Ray Yao

\-------------------------------------------------------------------------------

textarea input syntax:

<textarea  name="xxx"  rows="num"  cols="num">

// "textarea" type is used to input data in a text area.

// "rows" specifics the number of rows.

// "cols" specifics the number of columns.

e.g.

<html>

<form action="" method="POST">

<textarea name="book" rows="3"  cols="20"></textarea\>

<p><input type="submit" value="Submit"></p>

</form>

</html>

<?php

$book = $\_POST\['book'\];

echo "$book";

?>

// Output:

 ![](image_rsrc71G.jpg)

Scala in 8 Hours

\-------------------------------------------------------------------------------

time() syntax:

time()

// Return the current Unix timestamp (seconds) since the Unix Epoch

(from January 1st, 1970, 00:00:00 GMT to now)

e.g.

var\_dump(time());

// Output:   int(1669305569)

\-------------------------------------------------------------------------------

trait syntax:

<?php   trait TraitName{…}  ?>      // declare a trait

<?php   class MyClass{ use TraitName; }   ?>      // use the trait

// Trait is used to define a method that can be used in multiple classes.

// Trait enables programmers to reuse a method in different classes.

e.g.

<?php

trait myTrait {    // declare a trait

public function myFun() {

echo "This is a trait sample";

}}

class MyClass {

use myTrait;     // use the trait

}

$obj = new MyClass();

$obj\-\>myFun();

?>

// Output:   This is a trait sample

\-------------------------------------------------------------------------------

trigger\_error() syntax:

trigger\_error("message")

// Triggered by an error and show an error message.

e.g.

$var = -100;

if($var<0){trigger\_error("Variable value must > 0 ");}

// Output:

Notice: Variable value must > 0 in /server/script.php on line 3.

\-------------------------------------------------------------------------------

trim() syntax:

trim($str, "characters");  // remove string characters in both sides

trim($str);    // remove string whitespaces in both sides

e.g.

$str1 = "ABC 123"; $str2 = "   Hi, My friends!   ";

echo trim($str1,"A3")." ";     // remove A and 3

echo trim($str2);      // remove spaces in both sides

Output:   BC 12    Hi, My friends!

\-------------------------------------------------------------------------------

try / throw / catch() syntax:

try{…}    // contain some codes may cause exception

throw new Exception("message");  // throw an exception

catch{…}    // catch and handle the exception

e.g.

<?php

function myFun($num){

if($num<0){

throw new Exception("The variable value must be greater than 1");

}      // throw an exception

return true;

}

try{

myFun(-100);    // call the function

echo 'No this text is output if an exception has been thrown';

}

catch(Exception $e){     // catch the exception

echo $e\-\>getMessage();   // show the exception message

}

?>

// Output:   The variable value must be greater than 1

\-------------------------------------------------------------------------------

ucfirst() syntax:

ucfirst("string")

// Covert the first character of the string to uppercase.

e.g.

echo ucfirst("jQuery in 8 Hours");

// Output:   JQuery in 8 Hours

\-------------------------------------------------------------------------------

ucwords() syntax:

ucwords("string")

// Convert the first character of each word in a string to uppercase.

e.g.

echo ucwords("c# cheat sheet");

// Output:   C# Cheat Sheet

\-------------------------------------------------------------------------------

uniqid() syntax:

uniqid();

// Return a unique ID according to the current time in microseconds

e.g.

echo uniqid();

// Output:   637fc503919e3

\-------------------------------------------------------------------------------

unlink() syntax:

unlink("filename");

// Delete a file

e.g.

unlink("myFile.txt");

// Remove the "myFile.txt"

\-------------------------------------------------------------------------------

unserialize() syntax:

unserialize($serialized\_data)

// Convert serialized data back to original value.

e.g.

$var = serialize(array("ant", "bee", "cat", "dog"));

echo $var;

$arr = unserialize($var);

print\_r($arr);

// Output:   a:4:{i:0;s:3:"ant";i:1;s:3:"bee";i:2;s:3:"cat";i:3;s:3:"dog";}

Array(\[0\] => ant    \[1\] => bee    \[2\] => cat    \[3\] => dog)

\-------------------------------------------------------------------------------

unset() syntax:

unset($variable)

// Remove the value of the $variable

e.g.

$str = "Hi, My friend!";

unset($str);

echo "After unset, the 'str' value is: " . $str;

// Output:   After unset, the 'str' value is:

\-------------------------------------------------------------------------------

update table syntax:

$sql="update table-name set column-name=value where id=int";

$query=mysqli\_query( $con, $sql);  

// "update table-name set column-name=value where id=int" can update a value in a specified column of the table.

// $query=mysqli\_query($con, $sql) executes the query.

// "$con" is the connection to MySql server. (See mysqli\_connect()).

e.g.

<?php

$con= mysqli\_connect( "localhost", "root", "12345678" );

if( $con ) {     // if connect MySQL server successfully

echo  " Connect successfully! ";

}

$select=mysqli\_select\_db( $con, "myDB" );

if( $select ) {    // if select database "myDB" successfully

echo  " Select myDB successfully!<br> ";

}      // assume that myDB has a table "colortable"

$sql="update colortable set color5='sky' where id =1 ";

// set "sky" value to color5 column where id is 1

$query=mysqli\_query( $con, $sql);   // run query

if( $query ) {

echo  " Update successfully! ";

}

?>

// Output:

Connect successfully!  Select myDB successfully!  
Update successfully!

\-------------------------------------------------------------------------------

update table syntax:

update TableName set field1 = value1, field2 = value2

where field = value;

// Update fields’ values of a table in a database.

// “where field = value” can select a record to update fields.

e.g.

\# 1. Given the current status of the table “books” as follows:

use library;

select \* from books;

![](image_rsrc71H.jpg)

\# 2. Update the values of the specified fields:

update books set pages = 200, price = 13.99, publish = 2018

where title = "Java";

update books set pages = 190, price = 12.88, publish = 2019

where title = "Ajax";

select \* from books;

![](image_rsrc71J.jpg)

// “where title = "Java";” selects a record whose title is “Java” to update three fields (pages, price, publish).

// “where title = "Ajax";” selects a record whose title is “Ajax” to update three fields (pages, price, publish).

\-------------------------------------------------------------------------------

urldecode() syntax:

urldecode("encoded\_data")

// Decode the encoded data back to the original data.

e.g.

$encode\_data = urlencode("https://www.amazon.com/");

echo $encode\_data."\\n";

$decode\_data = urldecode($encode\_data);

echo $decode\_data;

// Output:   https%3A%2F%2Fwww.amazon.com%2F

https://www.amazon.com/

\-------------------------------------------------------------------------------

urlencode() syntax:

urlencode("data")

// Encode the specified data.

e.g.

echo urlencode("https://www.amazon.com/");

// Output:   https%3A%2F%2Fwww.amazon.com%2F

\-------------------------------------------------------------------------------

Use Database syntax:

use DatabaseName;

// Select a database in mysql server.

e.g.

mysql> use myDatabase;

Database changed

// “use myDatabase;” specifies to use a database named “myDatabase”.

// “Database changed” is responding message from the server.

\-------------------------------------------------------------------------------

usleep() syntax:

usleep(microseconds)

// Delay running the current code for a specified microseconds

e.g.

usleep(3000000);

// Pause for 3000000 microsecond before continuing.

\-------------------------------------------------------------------------------

variable syntax:

$variable =  value;

// variable name starts with "$" symbol.

e.g.

$var = 100;    // define a variable

$abcde = "Hello World";     // define a variable

$my\_variable = "Number1";    // define a variable

echo ( "$var  $abcde  $my\_variable");

// Output:   100  Hello World  Number1

\-------------------------------------------------------------------------------

var\_dump() syntax:

var\_dump($var);

// Return the type and value of a variable

e.g.

$x = 100;   var\_dump($x);

$y = 3.14;    var\_dump($y);

// Output:    int(100)     float(3.14)

\-------------------------------------------------------------------------------

where condition syntax:

SELECT columnName FROM tableName WHERE columnName operator value 

// Extract only those records that meet with the specified condition

e.g.

$sql = "SELECT id, firstname, lastname FROM myTable WHERE id='1001'";

// Return the record where id is 1001

\-------------------------------------------------------------------------------

while Loop syntax:

while ( test-expression ) {  // some php codes in here;  }

// Loop through a block of code if the specified condition is true.

e.g.

$counter=0;

while ($counter < 8){   // loop at most 8 times

echo "&";

$counter++;    // increase 1 every loop

}

// Output:   &&&&&&&&

\-------------------------------------------------------------------------------

wordwrap() syntax:

wordwrap($string, length, "\\n");

// Wrap a string to a new line when it reaches a specific length.

e.g.

$str = "'Google Sheet in 8 Hours' is a very good book.";

echo wordwrap($str,18,"\\n");    // at most 18 characters each line

// Output:

'Google Sheet in 8

Hours' is a very

good book.

\-------------------------------------------------------------------------------

xml dom parser syntax:

$xmlObj = new DOMDocument();     // create a dom document object  
$xmlObj\-\>load("myFile.xml");     // load a xml file  
print $xmlObj\-\>saveXML();     // print out the contents of an xml file

// Get data from an xml file, and print out contents according to nodes.

e.g.

1. Assume that the content of myFile.xml is:

<?xml version='1.0' encoding='UTF-8'?>

<note>

<from>Ray Yao</from>

<greeting>Hi, My friend!</greeting>

</note>

2.

<?php  
$obj = new DOMDocument();  
$obj\-\>load("myFile.xml");  
print $obj\-\>saveXML();  
?>

// Output:   Ray Yao   Hi, My friend!

# Appendix

PHP Reserved Words Chart

| and || array( ) || break |
| --- | --- | --- |
| case || const || continue |
| default || do || echo( ) |
| else || else if || empty( ) |
| eval( ) || exception || exit( ) |
| extends || false || for |
| function || foreach || global |
| if || include( ) || include\_once( ) |
| isset( ) || list( ) || new |
| null || or || print( ) |
| require( ) || require\_once( ) || return( ) |
| static || switch || true |
| unset( ) || xor || while |

PHP Escaping Characters Chart

| \\n || outputs content to the next new line. |
| --- | --- |
| \\r || makes a return |
| \\t || makes a tab |
| \\' || outputs a single quotation mark. |
| \\" || outputs a double quotation mark. |

PHP Predefined Characters Chart

| Predefined Chars || Becomes |
| --- | --- |
| &  (ampersand) || &amp; |
| "   (double quote) || &quot; |
| '   (single quote) || &#039; |
| <   (less than) || &lt; |
| \>   (greater than) || &gt; |

PHP File Opening Mode Chart

| Mode || Operation |
| --- | --- |
| r || open file for reading only, from the beginning. |
| r+ || open file for reading & writing, from the beginning. |
| w || open file for writing only, clear original content. |
| w+ || open file for writing & reading, clear original content. |
| a || open file for writing only, append new content. |
| a+ || open file for reading & writing, append new content. |
| x || create a new file for writing only. |
| x+ || create a new file for reading & writing. |

PHP Email Functions Chart

mail(to,subject,message,headers,parameters)

| Arguments || Descriptions |
| --- | --- |
| to || The receiver / receivers of the email |
| subject || The subject of the email |
| message || The message to be sent, limit 70 chars per line |
| headers || The headers, such as From, Cc, and Bcc |
| parameters || The additional parameter of the email program |

PHP Filter Functions Chart

| Function || Description |
| --- | --- |
| filter\_has\_var() || checks whether a variable of a specified input exist |
| filter\_id() || returns the filter id of a specified filter name |
| filter\_input() || gets a value from form input and optionally filters it |
| filter\_input\_array() || gets values from form input and optionally filters them |
| filter\_list() || returns a list of all supported filter names |
| filter\_var() || filters a variable with a specified filter |
| filter\_var\_array() || gets multiple variables and filter them |

PHP File Permission Chart

| Number || Permission |
| --- | --- |
| 0 || cannot read, write or execute |
| 1 || can only execute |
| 2 || can only write |
| 3 || can write and execute |
| 4 || can only read |
| 5 || can read and execute |
| 6 || can read and write |
| 7 || can read, write and execute |

PHP String Format Chart

| Symbol || Represent |
| --- | --- |
| %% || percent sign |
| %b || binary number |
| %c || the character according to the ascii value |
| %d || signed decimal number (negative, zero or positive) |
| %e || scientific notation using a lowercase (e.g.1.2e+2) |
| %E || scientific notation using a uppercase (e.g.1.2e+2) |
| %u || unsigned decimal number (equal to or greater than 0) |
| %f || floating-point number (local settings aware) |
| %F || floating-point number (not local settings aware) |
| %g || shorter of %e and %f |
| %G || shorter of %e and %f |
| %o || octal number |
| %s || string |
| %x || hexadecimal number (lowercase letters) |
| %X || hexadecimal number (uppercase letters) |

PHP Data & Time Format Chart

| Format || Description || Example |
| --- | --- | --- |
| a || 'am' or 'pm' lowercase || pm |
| A || 'AM' or 'PM' uppercase || PM |
| d || Day of month, a number with leading zeroes || 18 |
| D || Day of week (three letters) || Thu |
| F || Month name || January |
| h || Hour (12-hour format - leading zeroes) || 11 |
| H || Hour (24-hour format - leading zeroes) || 23 |
| g || Hour (12-hour format - no leading zeroes) || 11 |
| G || Hour (24-hour format - no leading zeroes) || 23 |
| i || Minutes ( 0 - 59 ) || 23 |
| j || Day of the month (no leading zeroes || 18 |
| l || Day of the week || Monday |
| L || Leap year ('1' for yes, '0' for no) || 1 |
| m || Month of year (number - leading zeroes) || 1 |
| M || Month of year (three letters) || May |
| n || Month of year (number - no leading zeroes) || 3 |
| s || Seconds of hour || 18 |
| U || Time stamp || 968292368 |
| y || Year (two digits) || 08 |
| Y || Year (four digits) || 2006 |
| z || Day of year (0 - 365) || 206 |
| Z || Offset in seconds from GMT || +5 |

PHP Data Type Chart

| Type || Description |
| --- | --- |
| String || characters within double or single quotation. |
| Integer || numbers without decimal point. |
| Boolean || a value with true or false. |
| Float || numbers with decimal point. |

mysqli\_xxx\_xxx (  ) Chart

| mysqli\_affected\_row ( )Returns the number of row affected by query |
| --- |
| mysqli\_close ( )Closes the connection with MySQL server |
| mysqli\_connect ( )Creates an initial connection with MySQL server |
| mysqli\_create\_db ( )Creates a database on the MySQL server |
| mysqli\_data\_seek ( )Adjusts the result pointer to a random row in the results |
| mysqli\_db\_query ( )This function was deprecated in PHP 5.3.0 |
| mysqli\_error ( )Returns a string with the error description |
| mysqli\_fetch\_array ( )Return an indexed and associative array that contains rows of a table. |
| mysqli\_fetch\_assoc ( )Return an associative array that contains rows of a table. |
| mysqli\_fetch\_row ( )Return an indexed array that contains rows of a table. |
| mysqli\_free\_result ( )Clears the system memory associated with the result |
| mysqli\_get\_server\_info ( )Returns a string with the MySQL server version |
| mysqli\_num\_rows ( )Returns the number of rows in the result set |
| mysqli\_query ( )Submits a query to the database on the server |
| mysqli\_real\_escape\_string ( )Escapes special characters in a string for MySQL |
| mysqli\_result ( )Returns a string of one cell from a MySQL result set |
| mysqli\_select\_db ( )Selects the database to use by database name |

MySQL Database Commands Chart

| Commands || Descriptions |
| --- | --- |
| CREATE DATABASE database-name || create database |
| USE database-name || use a database |
| SHOW database-name || show a database |
| DROP database-name || remove a database |

MySQL Table Commands Chart

| Commands || Descriptions |
| --- | --- |
| CREATE TABLE  table-name || create table |
| SHOW TABLE || show all tables |
| DESCRIBE || show fields property |
| SHOW COLUMNS FROM table-name || show a field property |
| SHOW INDEX FROM table-name || list index field property |
| ALTER TABLE table-name || change data of a field |
| DROP TABLE table-name || remove a table |
| OPTIMIZE table-name || optimize a table |

MySQL Operation Commands Chart

| Commands || Descriptions |
| --- | --- |
| SELECT field FROM table WHERE condition || query data |
| INSERT INTO table ( field ) VALUES (value) || insert data |
| DELETE FROM table WHERE condition || delete data |
| UPDATE table SET field = value WHERE condition || update data |
| PEPLACE INTO table (field ) VALUES (value) || replace data |

MySQL Data Type Chart

| Type || Depiction |
| --- | --- |
| int || An integer from -2147483648 to 2147483647 |
| decimal || A floating point number from -999.99 to 999.99. |
| double || A decimal number with double precision. |
| date || A date with the format YYYY-MM-DD |
| time || A time with the format HH:MM:SS |
| datetime || A digit with the format YYYY-MM-DD  HH:MM:SS. |
| year || A year with the YYYY format from 1901 to 2155 |
| timestamp || An automatic date & time of an event occurred. |
| char() || A string with fixed length up to 255 with padding. |
| varchar() || A string with variable length up to 255 no padding. |
| text || A string with length up to 65535 characters |
| blob || A variable with binary type. |
| enum || A single string value in a list. |
| set || A multiple string value in a list. |

MySQL Field Modifier Chart

| Modifier || Descriptions |
| --- | --- |
| AUTO\_INCREMENT || automatically generate a serial number |
| NUT NULL || cannot be empty value |
| NULL || can be empty value |
| UNIQUE || cannot not duplicate any entry |
| PRIMARY KEY || specify as a primary key |
| DEFAULT || specify a default value for a field |
| INDEX || specify an index field for table |

MySQL System Function Chart

| Functions || Returns |
| --- | --- |
| cast(v as type) || Return the converted data type |
| connection\_id() || Return the connecting id of the server |
| database() || Return the name of the current database |
| if(expr,m,n) || If expr is true, return m. If false, return n. |
| ifnull(m,n) || If m is not null, return m, otherwise return n |
| nullif(m, n) || If m equals n, return null, otherwise return m |
| user() || Return the name of the current user |
| version() || Return the version number of the database |
| show processlist || Display the id, user, host, db, command…… |

MySQL Numeric Function Chart

| Functions || Returns |
| --- | --- |
| abs(n) || absolute value of n |
| avg(field) || average value of a field |
| ceiling(n) || the closest integer above n |
| cos(n) || cosine of n |
| exp(n) || exponential value of n |
| floor(n) || the closest integer below n |
| max(field) || maximum value of a field |
| min(field) || minimum value of a field |
| mod(m, n) || remainder of m divided by n |
| pi() || 3.141593 |
| radians(n) || degrees n converted to radians |
| rand(n) || random number between 0 to 1.0 |
| round(n) || the closest integer to n |
| sin(n) || sine of n |
| sqrt(n) || square root of n |
| tan(n) || tangent of n |

MySQL Datetime Function Chart

| Functions || Returns |
| --- | --- |
| current\_date() || the current date |
| current\_time() || the current time |
| current\_timestamp() || the current date and time |
| date(date) || the date of the date. e.g. 2020-01-18 |
| day(date) || the day of the date. e.g. 18 |
| dayname(date) || day name of the date. e.g. Saturday |
| hour(date) || the hour of the date |
| minute(date) || the minute of the date |
| month(date) || the month of the date |
| monthname(date) || month name of the date. e.g. January |
| now() || the current date and time |
| second(date) || the second of the date |
| year(date) || the year of the date |

MySQL Statement Chart

| alter table TableName add FieldName  type  modifier;(add a field) |
| --- |
| alter table TableName add primary key (FieldName);(add a primary key) |
| alter table TableName add unique (FieldName);(set unique property for a field) |
| alter table TableName alter FieldName set/drop default;(set or remove default value for a field) |
| alter table TableName change FieldName1 FieldName2;(change field name) |
| alter table TableName drop FieldName;(remove a field) |
| 

## alter table TableName drop FieldName;

(remove a field) |
| alter table TableName drop primary key;(remove the primary key) |
| alter table TableName modify FieldName type modifier;(modify data type or modifier) |
| begin;(start a transaction) |
| call ProcedureName;(call the stored procedure) |
| commit;(execute a transaction) |
| count (distinct FieldName)(count the records with unique values in the specified field.) |
| count (FieldName)  (count the non-empty records in the field) |
| count(\*)   (count all records in the table) |
| 

## create database DatabaseName;

(create a new database) |
| 

## create database if not exists DatabaseName;

(create a database) |
| create table if not exists NewTableselect \* from OldTable;(copy a whole table) |
| 

## create table if not exists TableName (col1 type1, col2 type2);

(create a table) |
| create table TableName (col1  type1, col2  type2, col3  type3);

## (create a table)

 |
| create view ViewName (FieldNames) as select statements;(create a view) |
| create view ViewName (FieldNames) as select statements;(alter a view) |
| delete from TableName where field = value;(delete a record) |
| 

## delete from TableName where id = int;

(remove a record) |
| delete from TableName;(delete all records) |
| 

## describe TableName;

(show the table format) |
| drop database DatabaseName;(remove a database) |
| 

## drop database if exists DatabaseName;

(remove a database) |
| drop procedure if exists  ProcedureName;(remove a stored procedure) |
| 

## drop table if exists TableName;

(drop a table) |
| drop table TableName;(remove a table) |
| drop view if exists ViewName;(remove a view) |
| engine=innodb;(use innodb database engine) |
| 

## explain TableName;

(know about the table format) |
| FieldName  primary key,(set a field as a primary key) |
| group by FieldName;(group data in the field) |
| having condition(filter the groups) |
| insert into TableName (field1, field2, field3)

## values (value1, value2, value3);

(input data into a table) |
| order by field asc;(sort the data in ascending order) |
| order by field desc;(sort the data in descending order) |
| order by FieldName;(sort the data in a field) |
| rename table old\_table\_name to new\_table\_name;(rename a table)(change an old table name to a new table name) |
| rollback;(cancel a transaction) |
| 

## select  \*  from TableName;

(show table data) |
| select  @variable\_name;        (show the variable value) |
| select \* from FieldName as alias;(set a field name) |
| select \* from TableNamewhere FieldName between…and…(show records in a certain range) |
| select \* from TableNamewhere FieldName  !=  value;(show records without a specified value) |
| select \* from TableNamewhere FieldName  less/more than value;(show records less/more than a specified value) |
| select \* from TableNamewhere expression1 and expression2;(show records that satisfy two conditions.) |
| select \* from TableNamewhere expression1 or expression2;(show records that satisfy one of the conditions.) |
| select \* from TableNamewhere FieldName in (value1, value2, value3);(show records in an available range) |
| select \* from TableNamewhere FieldName like “%value%”(show records containing a similar value with some characters) |
| select \* from TableNamewhere FieldName like “\_value\_”(show records containing a similar value with one character) |
| select \* from TableNamewhere FieldName regexp pattern(show records whose value matches the specified pattern) |
| select \* from TableNameorder by rand()limit n;(get random records) |
| select \* from TableName order by FieldName;(show sorted data in a field) |
| select \* from TableName where field = value;(show a specified record) |
| select \* from TableName1union allselect \* from TableName2union allselect \* from TableName3;(combine multiple select queries in one table) |
| select @variable\_name :\= value;(define a variable and show its value) |
| select alias1.field1, alias2.field2from table1 as alias1 join table2 as alias2on alias1.fieldname = alias2.fieldname;(show two joined tables’ data in one table) |
| select alias1.field1, alias2.field2from table1 as alias1 left join table2 as alias2on alias1.fieldname = alias2.fieldname;(show two joined tables’ data, including complete left-table data) |
| select alias1.field1, alias2.field2from table1 as alias1 right join table2 as alias2on alias1.fieldname = alias2.fieldname;(show two joined tables’ data, including complete right-table data) |
| select concat(field1, "separator" , field2) from TableName;(connect two or more fields together) |
| select count(\*) from TableName;(count all records in the table) |
| select count(distinct FieldName) from TableName;(show the records with unique values in the specified field.) |
| select count(FieldName) from TableName;(count the non-empty records in the field) |
| select distinct FieldName from TableName;(show the records with unique values in the specified field) |
| select Field, count(\*) from Table group by Field;(show the data grouped by fields) |
| select Field1, Field2, Field3 from table1, table2, table3;(show multiple tables in one table) |
| select field1, field2, field3 from TableName;(show specified fields) |
| select sum(FieldName) from TableName;.(sum up the value of the specified field) |
| set @variable\_name :\= value;    (define a variable) |
| set autocommit=0;(disable autocommit) |
| set autocommit=1;(enable autocommit) |
| 

## show databases;

(show all existing databases) |
| 

## show tables;

(show all the existing tables) |
| stored procedure;delimiter  //create procedure ProcedureName()beginselect statement;end  //delimiter; |
| table1 join table2(join table1 and table2) |
| table1 left join table2(join two table’s data, including complete left-table data) |
| table1 right join table2(join two table’s data, including complete right-table data) |
| update TableName set field1 = value1, field2 = value2

## where field = value;

(update fields) |
| update TableName set FieldName = value;(update the data for all records in a field) |
| 

## update TableName set FieldName = value;

(update the data for a specified record in a field) |
| 

## use DatabaseName;

(select a database) |
| where condition(filter the records) |

Cheat Sheet by Ray Yao

| [C# Cheat Sheet](https://author.to/C_Sharp_Cheat_Sheet)[C++ Cheat Sheet](https://mybook.to/C_Plus_cheat_sheet)[Java Cheat Sheet](https://author.to/Java_Cheat_Sheet)[JavaScript Cheat Sheet](https://mybook.to/JavaScript_cheat_sheet) |
| --- |