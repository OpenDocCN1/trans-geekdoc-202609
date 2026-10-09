One of the primary uses of a linked list is to produce a display of items in a different order. One approach would be to create an iteration of key value pairs, where the key represents the new order, and the value contains the value of the key in the primary list. Such a function might look like this:
function buildLinkedList (array $primary,
callable $makeLink)
{
$linked = new ArrayIterator ();
foreach ($primary as $key => $row) {
$linked->offsetSet ($makeLink ($row), $key);
}
$linked->ksort ();
return $linked;
}

We use an anonymous function to generate the new key in order to provide extra flexibility. You will also notice that we do a sort by key (ksort ( )) so that the linked list iterates in key order.

All we need to do to use the linked list is to iterate through it, but produce results from the primary list, $customer in this example:
foreach ($linked as $key => $link) {
$output .= printRow ($customer [$link]]);
}

Note that in no way do we touch the primary list. This allows us to generate multiple linked lists, each representing a different order, while retaining our original set of data.

Another important use of a linked list is for the purposes of filtering. The technique is similar to that shown previously. The only difference is that we expand the buildLinkedList () function, adding a filter column and filter value:
function buildLinkedList (array $primary,
callable $makeLink,
$filterCol = NULL,
$filterVal = NULL)
{
$linked = new ArrayIterator ();
$filterVal = trim ($filterVal);
foreach ($primary as $key => $row) {
if ($filterCol) {
if (trim ($row [$filterCol] )) == $filterVal) {
$linked->offsetSet ($makeLink ($row), $key);