where RS indicates the recommendation score and n represents the number of recommendations received from neighbor nodes. The average IDTS is calculated for the network using equation 5.

AvgIDTS (t1, t2) = (IDTS1 <t1, t2> + IDTS2 <t1, t2> + ......+ IDTS <t1, t2>)/n (5)

where n indicate the total number of nodes available in the network.

# 2.4.2.6 Rules

In this work, IF...THEN rules are framed by using the direct trust, indirect trust, energy, and mobility for identifying the eligible node to participate in the routing process.

+   **Rule 1:**
+   If (DTSi (t1, t2) < AvgDTS) AND
+   (DTSi (t1, t2) < AvgIDTS) AND
+   (Mob (t1, t2) < AvgMob) AND
+   (En (t1, t2) < AvgEn) Then
+   Node is LOW & Not Eligible to participate in the routing process.

+   **Rule 2:**
+   If (DTSi (t1, t2) > AvgDTS) AND
+   (IDTSi (t1, t2) > AvgIDTS) AND
+   (Mob (t1, t2) < AvgMob) AND
+   (En (t1, t2) < AvgEn) Then
+   Node is LOW MEDIUM & Eligible to participate in the routing process.

+   **Rule 3:**
+   If (DTSi (t1, t2) > AvgDTS) AND
+   (IDTSi (t1, t2) > AvgIDTS) AND
+   (Mob (t1, t2) > AvgMob) AND
+   (En (t1, t2) > AvgEn) Then
+   Node is MEDIUM & Eligible to participate in the routing process.

+   **Rule 4:**
+   If (DTSi (t1, t2) > AvgDTS) AND
+   (IDTSi (t1, t2) > AvgIDTS) AND
+   (Mob (t1, t2) < AvgMob) AND
+   (En (t1, t2) > AvgEn) Then