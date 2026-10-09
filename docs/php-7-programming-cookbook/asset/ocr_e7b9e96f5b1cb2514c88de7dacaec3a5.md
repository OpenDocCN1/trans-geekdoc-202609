```
namespace Application\Filter;
class Filter extends AbstractFilter
{
    // code
}
```

+   17. Within this class we define a core process() method that scans an array of data and applies filters as per the array of assignments. If there are no assigned filters for this data set, we simply return NULL:
public function process(array $data)
{
    if (!isset($this->assignments)
        && count($this->assignments)) {
        return NULL;
    }
}

+   18. Otherwise, we initialize $this->results to an array of Result objects where the $item property is the original value from $data, and the $messages property is an empty array:
foreach ($data as $key => $value) {
    $this->results[$key] = new Result($value, array());
}

+   19. We then make a copy of $this->assignments and check to see if there are any global filters (identified by the '*' key). If so, we run processGlobal() and then unset the '*' key:
$toDo = $this->assignments;
if (isset($toDo['*'])) {
    $this->processGlobalAssignment($toDo['*'], $data);
    unset($toDo['*']);
}

+   20. Finally, we loop through any remaining assignments, calling processAssignment():
foreach ($toDo as $key => $assignment) {
    $this->processAssignment($assignment, $key);
}

+   21. As you will recall, each assignment is keyed to the data field, and represents an array of callbacks for that field. Thus, in processGlobalAssignment() we need to loop through the array of callbacks. In this case, however, because these assignments are global, we also need to loop through the entire data set, and apply each global filter in turn:
protected function processGlobalAssignment($assignment, $data)
{
    foreach ($assignment as $callback) {