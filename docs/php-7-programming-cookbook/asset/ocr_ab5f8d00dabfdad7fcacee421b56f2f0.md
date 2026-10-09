After that, define teardown(), which removes the test data and confirms that the query for id = 1 comes back as FALSE:

```
public function teardown()
{
$result = $this->visitorOps->removeById(1);
$result = $this->visitorOps->findById(1);
$this->assertEquals(FALSE, $result);
unset($this->visitorOps);
}
```

The first test is for findAll(). First, confirm the data type of the result. You could take the topmost element using current(). We confirm there are five elements, that one of them is name, and that the value is the same as that in the test data:

```
public function testFindAll()
{
$result = $this->visitorOps->findAll();
$this->assertInstanceOf(Generator::class, $result);
$top = $result->current();
$this->assertCount(5, $top);
$this->assertArrayHasKey('name', $top);
$this->assertEquals($this->testData['name'], $top['name']);
}
```

The next test is for findById(). It is almost identical to testFindAll():

```
public function testFindById()
{
$result = $this->visitorOps->findById(1);
$this->assertCount(5, $result);
$this->assertArrayHasKey('name', $result);
$this->assertEquals($this->testData['name'], $result['name']);
}
```

You do not need to bother with a test for removeById() as this is already done in teardown(). Likewise, there is no need to test runSql() as this is done as part of the other tests.

# ### Using mock classes

First, define a VisitorService service class as described in steps 2 and 3 in this subsection. Next, define a VisitorOpsMock mock class, which is discussed in steps 4 to 7.