```
public function parseFile($filename, $config, $encoding, $use_include_path=false) {
    return parent::parseFile(
        $filename,
        array_merge($this->_default, $config),
        $encoding,
        $use_include_path
    );
}

public function parseString($filename, $config, $encoding, $use_include_path=false) {
    return parent::parseString(
        $filename,
        array_merge($this->_default, $config),
        $encoding,
        $use_include_path
    );
}
?>
```

+   - `array_merge` is used to consolidate default parameter values in the `$._default` property into the specified `$config` array. Any parameters specified in the original `$config` array will take precedence over corresponding parameters specified in `$_default`.

+   - `parseFile` and `parseString` pass the modified `$config` parameter with all other provided parameters to their respective methods in the tidy class and return the resulting return value.

# ## Options

Tidy includes a large number of configuration options, only a few of which are relevant in the context of this book.

Two options deal with output formats applicable for web scraping: `output.html` and `output.xhtml`. Both are specified as boolean values. These options are mutually exclusive, meaning that only one can be set to `true` at any given time. Generally `output.xhtml` is preferable, but may not always be feasible to use. It's important to