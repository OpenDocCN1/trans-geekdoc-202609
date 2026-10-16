# 25. ADDING RESERVATION FEATURES

```
145.     <h3>No Movie Details :-</h3>
146.         <?php
147.         }
148. 
149.         else: // Unintended page link - No movie to reseve, redirect back to index
150. 
151.             header("Location: " . dirname($_SERVER['PHP_SELF']));
152.             exit();
153.         endif;
154.         ?>
155.     </div>
156. </div>
157. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
158.         integrity="sha384-q8i/X+965DzO0rT7abK0..." 
159.         crossorigin="anonymous"></script>
160. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
161.         integrity="sha384-wHAiF1qPbEpJL1lv..." 
162.         crossorigin="anonymous"></script>
163. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
164.         integrity="sha384-B0Uglyr..." 
165.         crossorigin="anonymous"></script>
166. </body>
167. </html>
```

# Adding Cart to Navigation Menu

Now that we can reserve movies and put them into a shopping cart, let’s add a shopping cart icon in the upper right-hand corner of the navigation menu (Figure 25.16). We can also add a numerical representation of how many items are in the cart when a user adds a movie to their cart, as shown in Figure 25.17.

When the user selects this shopping cart icon, the application navigates to a shoppingcart.php script we create in the following section. But first, let’s add the code to navmenu.php for our shopping cart.

We want the shopping cart icon to show if a user with user privileges is logged in and to indicate the number of items next to the icon if there is more than one item in the cart. We also want this icon to be a right-side menu item in the navbar to separate it from the other navigation links.

![](bbox=[0.1, 0.74, 0.74, 0.88])

![](bbox=[0.77, 0.74, 0.92, 0.85])