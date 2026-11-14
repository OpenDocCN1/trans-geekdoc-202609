```
views/noproducts.html
1 <!--- box begin -->
2 <div class="box alt">
3     <div class="left-top-corner">
4         <div class="right-top-corner">
5             <div class="border-top"></div>
6         </div>
7     </div>
8 <div class="border-left">
9     <div class="border-right">
10    <div class="inner">
11    <h2><?php echo $category; ?><h2>
12    Unfortunately there are no products to list in this category. Please
        use the links at the top of the page to continue shopping. We
        apologize for the inconvenience.
13    </div>
14    </div>
15    </div>
16 <div class="left-bot-corner">
17    <div class="right-bot-corner">
18        <div class="border-bot"></div>
19    </div>
20 </div>
21 </div>
22 <!--- box end -->
```

# # INDICATING AVAILABILITY

For the list of coffee products, the stored procedure only retrieves those currently in stock. For the other products, though, the stock is currently represented as the quantity on hand (see Figure 8.6), which you probably don't want to show the customer. Instead, let's create a function that will display the availability in a friendlier and purchase-encouraging, manner. The function will be defined in a new script named product_functions.inc.php.

+   1. Create a new PHP script in your text editor or IDE to be named product_functions.inc.php and stored in the includes directory.
+   <?php