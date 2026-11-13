```
->Item[$i]->ItemAttributes->ListPrice
->FormattedPrice . "]]></price>";
$xml .= "<t\t<thumb>" . $xmlResponse->Items->Item[$i]
 ->SmallImage->URL . "</thumb>";
$xml .= "</book>";
```

**CAUTION** The data to generate the XML is one line per $xml variable; the wrapping is to fit this page and can potentially break your code.

The last portion of the PHP for this example creates a header type so XML readers know the format that is being sent. Then it finally outputs it to the screen.

```
header ("content-type: text/xml");
print $xml;
```

The Flash (ActionScript) required for the application is all in external classes. This is done because it is easier to manage and maintain moving forward.

**CROSS-REF** If you need a more in-depth explanation of classes, I strongly recommend you read Chapter 9.

The Flash File (FLA) for this application consists of a simple design with a search box and button. The main class, BookSearch, is assigned as the document class and is responsible for managing the overall application. Here is the class skeleton, which gives you an idea of what methods and properties are used to create this application.

```
package
{
import flash.display.MovieClip;
import flash.events.*;
import flash.net.*;

public class BookSearch extends MovieClip
{
public var webServiceURL:String;
private var bookItems:Array;
private var bookItemsContainer:MovieClip;

public function BookSearch() {}

public function searchHandler(e:MouseEvent):void {}

public function loadSearchResults(terms:String):void {}

public function loadedResultsHandler(e:Event):void {}

private function removeOldResults():void {}
}
}
```