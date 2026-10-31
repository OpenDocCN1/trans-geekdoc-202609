```
function FetchProduct ($product_id=0)
{
    if (!empty($product_id))
    {
        $this->product_id = $product_id;
    }
    if (empty($this->product_id))
    {
        $this->error = "no product_id specified for fetch";
        return FALSE;
    }
    $result = safe_query("select * from products
        where product_id = $this->product_id
    ");
    if (!$result)
    {
        return FALSE;
    }
    $row = mysql_fetch_array($result,MYSQL_ASSOC);
    $this->Construct($row);
    return TRUE;
}
```

Notice the use of $this->error. By using defining an error in this way, in our scripts we can do the following:

```
$p = new Product;
if (!$p->FetchProduct(1))
{
    echo $p->error;
} else{
    echo "The product name is: $p->product";
}
```

if the fetch didn’t work out. The method will return FALSE, and you will have access to a meaningful error message.

# METHOD LOADPRODUCT()

As mentioned earlier, this is the method that will create the structure seen in Figure 10-12. If you look at that figure, you will see there is quite a bit of information: the number of associated styles, the number of associated sub-styles. Then there is the array that contains Style objects.

```
function LoadProduct ($product_id=0)
{
    $this->FetchProduct($product_id);
```