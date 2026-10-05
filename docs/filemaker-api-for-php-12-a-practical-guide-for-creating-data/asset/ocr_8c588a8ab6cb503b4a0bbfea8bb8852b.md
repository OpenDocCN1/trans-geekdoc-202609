Find all the records using the Subsummary Report layout. Since this is a basic example, I didn't want to complicate the process with a form to find records. The point isn't how to find records, the point is how to generate a subsummary report.

```
<php
$request = $fm->findAllCommand('Subsummary Report');
```

Before we find the request we'll need to sort the records. The problem is that the API doesn't provide us with a method to reorder the results based on a summary field. That means we'll have to create the Subsummary Report script in the database that will sort the records on the layout to display the report as intended. Then we'll run the script using the setScript method. This method will run the script after the find request is performed and FileMaker Server sorts the records in default creation order. Then we can execute the request.

```
$request->setScript('Subsummary Report');
$result = $request->execute();
```

FileMaker Syntax: setScript($ScriptName, ScriptParameter)

![](bbox=[0.118, 0.345, 0.215, 0.383])

Next, for any errors returned by FileMaker Server.

```
if (FileMaker::getError($result))
{
  echo "<p>Error: " . $result->getMessage() . "</p>";
exit;
}
```

Store the contents of the records returned by FileMaker Server in the $records variable.

```
$records = $result->getRecords();
```

Start the display of the data by creating the table with static header section.

```
echo '<table border="1">
<tr><th>Subsummary Report/</th></tr>
<tr>
  <th>SalesPerson</th>
  <th>Amount</th>
</tr>';
```

Now we can loop through the data in the $records variable by using the PHP method. This is where we'll need to think logically about how display the Subtotal and Grand Total values, as these values don't exist in the Body of the FileMaker layer.

```
foreach ($records as $record)
```

The Subtotal row comes first in the code. However, it appears to be out of order from a logical perspective. It will make much more sense once you find the end of the loop. The script will skip the Subtotal until the first loop because the $salesperson variable won't be created until the end of the first loop. Then it checks subsequent loop for the last $salesperson. If the $salesperson doesn't match the SalesPerson in the loop you can assume you're about to start a new subsummary section. Then you can add the Subtotal table row. This is a very similar technique that I utilize all the time with lists of FileMaker records where I compare the current record against the previous record to perform some task when the records change values.

```
if(!empty($salesperson) and $salesperson != $record->getField('SalesPerson'))
{}
```