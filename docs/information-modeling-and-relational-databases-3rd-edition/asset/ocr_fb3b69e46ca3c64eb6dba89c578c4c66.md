![](bbox=[0.29, 0.1, 0.69, 0.4])

Each of the following requests applies to the **same** database population as shown (i.e., treat each request as if it was the *first* to be made on this population). For each request, indicate the response of the conceptual information processor (CIP). If the request is legal, write “accepted”. Otherwise, indicate a constraint violated (e.g., “C2 violated”).

+   (a) add: a1 S b1
+   (b) add: a3 R b3
+   (c) add: V a1 b1 d2
+   (d) add: a1 R b2
+   (e) add: a1 R b3
+   (f) add: a2 S b3
+   (g) delete: b3 T c3
+   (h) begin
+   add: b4 T c1
+   add: b4 U c2
+   end
+   (i) begin
+   add: b4 T c3
+   add: b4 U c2
+   end
+   (j) begin
+   add: V a1 b2 d2
+   add: V a1 b3 d2
+   end
+   (k) add: d1 W d3
+   (l) add: d1 W d1

5. Schematize the following output report. Here, “bordering” means sharing a land border. In this sense, countries such as Australia have no bordering nations.

| Nation | Bordering nations |
| :--- | :--- |
| Australia | |
| Belgium | France, Germany, Luxembourg, Netherlands |
| France | Belgium, Germany, Italy, Luxembourg, Spain, Switzerland |
| ... | ... |

6. (a) Which, if any, of asymmetry and intransitivity are implied by acyclicity? (b) Convince yourself that the recursive definition of acyclicity given earlier is correct. Model relationships of type R graphically, and consider the fact xRy as a directed line from x to y.