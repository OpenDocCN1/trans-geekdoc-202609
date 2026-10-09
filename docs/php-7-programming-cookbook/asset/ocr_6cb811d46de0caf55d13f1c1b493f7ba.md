. $this->imageFn);
    imagedestroy($im);

12. The entire construct is in a `try/catch` block. If an error or exception is thrown, we log the message and take the appropriate action:

```
} catch (\Throwable $e) {
    error_log(_METHOD . ':' . $e->getMessage());
    throw new \Exception(self::ERROR_IMAGE);
}
```

13. Finally, we define the methods required by the interface. Note that `getImage()` returns an HTML `<img>` tag, which can then be immediately displayed:

```
public function getLabel()
{
    return $this->label;
}
```

```
public function getImage()
{
    return sprintf('<img src="%%s/%%s" />',
        $this->imageUrl, $this->imageFn);
}
```

```
public function getPhrase()
{
    return $this->phrase->getPhrase();
}
```

# How it works...

Be sure to define the classes discussed in this recipe, summarized in the following table:

| Class | Subsection | The steps it appears in |
|---|---|---|
| Application\Captcha\Phrase | Generating a text CAPTCHA | 1 – 5 |
| Application\Captcha\CaptchaInterface |  | 6 |
| Application\Captcha\Reverse |  | 7 |
| Application\Captcha\Image | Generating an image CAPTCHA | 2 - 13 |