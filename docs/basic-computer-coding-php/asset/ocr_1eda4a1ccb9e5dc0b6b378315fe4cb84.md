```
$query = http_build_query($query)
} else {
$query = $sqs;
$queryString = $components['query'];
} elseif ($query) {
$queryString = http_build_query($query, '', '&');
}
$server['REQUEST_URI'] = $components['path'].($query ? '?'.$query : '');
$server['QUERY_STRING'] = $queryString;

return self::createRequestFromFactory($query, $request, $n
```

# CHAPTER 4

# PHP: STRING

> “String Theory describes energy and matter as being composed of tiny, wiggling strands of energy that look like strings. And the pitch of a string's vibration determines the nature of its effect.”

Roy H. Williams

# Learning Objectives

After studying this chapter, you will be able to:

+   - Define the basics of PHP string functions
- Know the use of parsing in PHP