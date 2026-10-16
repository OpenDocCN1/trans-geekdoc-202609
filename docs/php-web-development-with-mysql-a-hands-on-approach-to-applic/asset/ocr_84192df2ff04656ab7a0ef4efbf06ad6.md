# 15. DISPLAYING A LIST OF ITEM DETAILS

```
18. $result = mysqli_query($dbc, $query)
19.     or trigger_error('Error querying database movieListing', E_USER_ERROR);
20.
21.     if (mysqli_num_rows($result) == 1):
22.
23.         $row = mysqli_fetch_assoc($result)
24.     ?>
25. <h1><?= $row['title'] ?></h1>
26. <table class="table table-striped">
27.     <tbody>
28.         <tr>
29.             <th scope="row">Rating</th>
30.             <td><?= $row['rating'] ?></td>
31.         </tr>
32.         <tr>
33.             <th scope="row">Director</th>
34.             <td><?= $row['director'] ?></td>
35.         </tr>
36.         <tr>
37.             <th scope="row">Running Time (minutes)</th>
38.             <td><?= $row['running_time_in_minutes'] ?></td>
39.         </tr>
40.         <tr>
41.             <th scope="row">Genre</th>
42.             <td><?= $row['genre'] ?></td>
43.         </tr>
44.     </tbody>
45. </table>
46.     <?php
47.     else:
48.     ?>
49. <h3>No Movie Details :- (</h3>
50. <?php
51. endif;
52.     else:
53.     ?>
54. <h3>No Movie Details :- (</h3>
55. <?php
56. endif;
57. ?>
58. // ...
59. </body>
```

Figure 15.20 shows what our Movie Details page looks like now.

![](bbox=[0.48, 0.68, 0.92, 0.87])