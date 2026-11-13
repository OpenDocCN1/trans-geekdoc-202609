```
```
cartItemCount--;

if(cartItemCount == 0)
{
    noItemsTxt.visible = true;
}

updateList();
updateTotal();
}

public function updateList():void
{
    for(var i:uint=0; i < cartItemCount; i++)
    {
        cartContents[i].cartItem.setID(i);
        cartContents[i].cartItem.y =
            (i * cartItemHeight) + lineSpacing;
    }
}

public function updateTotal():void
{
    var total:Number = 0;
    for(var i:uint=0; i < cartItemCount; i++)
    {
        total += Number(cartContents[i].price) *
            Number(cartContents[i].cartItem.quantityTxt.text);
    }

    totalTxt.text = "$" + String(round2D(total));

    // tack on extra 0 if needed or two 0's
    if(totalTxt.text.indexOf('.') == -1)
    {
        totalTxt.appendText(".00");
    }
    else if(totalTxt.text.indexOf('.') + 2 ==
        totalTxt.text.length)
    {
        totalTxt.appendText("0");
    }
}

public function setGatewayURL(url:String):void
{
    gateway = url;
}

private function round2D(n:Number):Number
```
```