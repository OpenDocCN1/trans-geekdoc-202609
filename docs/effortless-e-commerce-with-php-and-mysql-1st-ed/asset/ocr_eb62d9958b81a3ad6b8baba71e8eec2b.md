If $row['sd'] is NULL (for any item in the order), then the entire order has not been shipped yet, and the flag variable should indicate such.

+   13. Complete the loop and the table:
+   } while ($row = mysqli_fetch_array($r));
+   echo '</tbody></table>';

After the contents of the loop are executed, the condition is checked. The specific condition is the fetching of another array from the query results. If another array can be found, the loop will be repeated again.

+   14. If the order hasn't entirely shipped, create the submit button:
+   if (!Shipped) {
+    echo '<div class="field"><p class="error">Note that actual payments will be collected once you click this button!</p>
+    <input type="submit" value="Ship This Order " class="button" />
+    </div>';
+   }

For orders that have completely shipped, no submit button will exist (Figure 11.14).

![](bbox=[0.34, 0.51, 0.72, 0.69])

Figure 11.14

+   15. Complete the form:
+   echo '</fieldset>
+   </form>';

+   16. Complete the mysql_num_rows() conditional:
+   } else { // No records returned!
+    echo '<h3>Error!</h3><p>This page has been accessed in error.
+    </p>';