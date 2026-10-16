# # Testable code

Testable code is decoupled and single purpose. To me it feels like there are two main concerns for this code

+   1. Retrieving the raw XML data
+   2. Decoding the XML data and applying our business logic (in this case strings.ToUpper on the <message>)

The first part is just copying the example from the standard lib.

The second part is where we have our business logic and by looking at the code we can see where the "seam" in our logic starts; it's where we get our io.ReadCloser. We can use this existing abstraction to separate concerns and make our code testable.

The problem with GetData is the business logic is coupled with the means of getting the XML. To make our design better we need to decouple them

Our TestGetData can act as our integration test between our two concerns so we'll keep hold of that to make sure it keeps working.

Here is what the newly separated code looks like

```
```go
type Payload struct {
	Message string `xml:"message"`
}

func GetData(data io.Reader) string {
	var payload Payload
	xml.NewDecoder(data).Decode(&payload)
	return strings.ToUpper(payload.Message)
}

func getXMLFromCommand() io.Reader {
	cmd := exec.Command("cat", "msg.xml")
	out, _ := cmd.StdoutPipe()
	return out
}
```
```