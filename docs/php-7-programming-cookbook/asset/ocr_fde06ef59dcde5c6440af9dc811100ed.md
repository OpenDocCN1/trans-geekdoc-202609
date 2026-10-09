```
```
$this->httpHeaders[$found] .= $value;
} else {
$this->httpHeaders[$name] = $value;
}
return $this;
}

public function withoutHeader($name)
{
$found = $this->findHeader($name);
if ($found) {
unset($this->httpHeaders[$found]);
}
return $this;
}
```
```

+   9. We then provide a series of useful header-related methods to confirm a header exists, retrieve a single header line, and retrieve a header in array form, as per PSR-7:

```
```
public function hasHeader($name)
{
return boolval($this->findHeader($name));
}

public function getHeaderLine($name)
{
$found = $this->findHeader($name);
if ($found) {
return $this->httpHeaders[$found];
} else {
return '';
}
}

public function getHeader($name)
{
$line = $this->getHeaderLine($name);
if ($line) {
return explode(',', $line);
} else {
return array();
}
}
```
```