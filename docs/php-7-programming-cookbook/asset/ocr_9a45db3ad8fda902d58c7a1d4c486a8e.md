> Objects could also be considered for conversion; however, it is difficult to render object methods in XML. Properties can be represented, however, by using the `get_object_vars()` function, which reads object properties into an array.

# **How to do it...**”

+   1.  First, we define an `Application\Parse\ConvertXml` class. This class will hold the methods that will convert from XML to a PHP array, and vice versa. We will need both the `SimpleXMLElement` and `SimpleXMLIterator` classes from the SPL:

    ```
    namespace Application\Parse;

    use SimpleXMLIterator;
    use SimpleXMLElement;

    class ConvertXml
    {
    }
    ```

+   2.  Next, we define a `xmlToArray()` method that will accept a `SimpleXMLIterator` instance as an argument. It will be called recursively and will produce a PHP array from an XML document. We take advantage of the `SimpleXMLIterator` ability to advance through the XML document, using the `key()`, `current()`, `next()`, and `rewind()` methods to navigate:

    ```
    public function xmlToArray(SimpleXMLIterator $xml) : array
    {
        $a = array();

        for( $xml->rewind(); $xml->valid(); $xml->next() ) {
            if(!array_key_exists($xml->key(), $a)) {
                $a[$xml->key()] = array();
            }

            if ($xml->hasChildren()) {
                $a[$xml->key() ][] = $this->xmlToArray($xml->current());
            }
            else{
                $a[$xml->key() ] = (array) $xml->current()->attributes();
                $a[$xml->key()][ 'value'] = strval($xml->current());
            }
        }
        return $a;
    }
    ```