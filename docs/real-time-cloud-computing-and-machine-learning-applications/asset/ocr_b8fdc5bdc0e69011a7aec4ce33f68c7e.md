# Server and Servlet Architectures for a Cloud-Based Real-Time ...

![](bbox=[0.237, 0.091, 0.762, 0.313])

Figure 7.34. Setting Servlet Name & Package.

3. After creating the servlet, the class shown in Figure 7.35 will appear in the editor.

```
```java
1
2
3 import java.io.IOException;
4
5 /**
6 * * Servlet implementation class Forecaster
7 */
8
9 //10 //
11
12 @WebServlet("/forecaster")
13 public class Forecaster extends HttpServlet {
14     public static final long serialVersionUID = 1L;
15
16
17
18
19     // @WebServlet(HttpServletServlet())
20     public Forecaster() {
21         super();
22         // TODO Auto-generated constructor stub
23     }
24
25
26
27
28
29     protected void doGet(HttpServletRequest request, HttpServletResponse response)
30         throws ServletException, IOException {
31         response.getWriter().append("Served at :").append(request.getPathInfo());
32     }
33
34
35
36
37     @WebServlet(HttpServletRequest)
38     protected void doPost(HttpServletRequest request, HttpServletResponse response)
39         throws ServletException, IOException {
40         // TODO Auto-generated method stub
41         doPost(request, response);
42     }
43
44
45 */
```
```

Figure 7.35. Default Servlet.

The "@WebServlet" annotation defines a servlet component in a web application. A URL pattern is also defined in the annotation. The line "@WebServlet("/forecaster") indicates that the servlet can be contacted on the URL http://localhost:8080/Network/Forecaster. The servlet is generated with a Constructor, the doGet() method, and the doPost() method. In doGet(), the parameters are appended to the URL and sent with header information. This does not happen in the case of doPost(). In doPost(), the parameters are sent separately. Since most of the web servers support only a limited amount of