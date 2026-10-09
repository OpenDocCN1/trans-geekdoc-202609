+   8. We then add a currency code lookup to the class constructor if the lookup class has been defined:

```
public function __construct($localeString = NULL,
                IsoCodesInterface $currencyLookup = NULL)
{
    // add this to the existing code:
    $this->currencyLookup = $currencyLookup;
    if ($this->currencyLookup) {
        $this->currencyCode =
            $this->currencyLookup
                ->getCurrencyCodeFromIso2CountryCode($this
                ->getCountryCode())
                ->currency_code;
    } else {
        $this->currencyCode = self::FALLBACK_CURRENCY;
    }
}
```

+   9. Then add the appropriate currency format and parse methods. Note that parsing currency, unlike parsing numbers, will return FALSE if the parsing operation is not successful:

```
public function formatCurrency($currency)
{
    return $this->getCurrencyFormatter()
        ->formatCurrency($currency, $this->currencyCode);
}

public function parseCurrency($string)
{
    $result = $this->getCurrencyFormatter()
        ->parseCurrency($string, $this->currencyCode);
    return ($result) ? $result : self::ERROR_UNABLE_TO_PARSE;
}
```

# How it works...

Create the following classes, as covered in the first several bullet points:

| Class | Bullet point discussed |
| Application\I18n\IsoCodes | 3 |
| Application\I18n\IsoCodesInterface | 4 |
| Application\I18n\IsoCodesDb | 5 |