Constants::STATUS_CODES[$statusCode] ?? '';
$this->httpHeaders = $headers;
$this->version = $this->onlyVersion($version);
if ($statusCode) $this->setStatusCode();
}

+   3.  We provide a nice way to set the HTTP status code, irrespective of any headers, using `http_response_code()`, available from PHP 5.4 onwards. As this work is on PHP 7, we are safe in the knowledge that this method exists:
    ```
    public function setStatusCode()
    {
        http_response_code($this->getStatusCode());
    }
    ```

+   4.  Otherwise, it is of interest to obtain the status code using the following method:
    ```
    public function getStatusCode()
    {
        return $this->status['code'];
    }
    ```

+   5.  As with the other PSR-7-based classes discussed in earlier recipes, we also define a `with` method that sets the status code and returns the current instance. Note the use of STATUS_CODES to confirm its existence:
    ```
    public function withStatus($statusCode, $reasonPhrase = '')
    {
        if (!isset(Constants::STATUS_CODES[$statusCode])) {
            throw new InvalidArgumentException(
                Constants::ERROR_INVALID_STATUS);
        }
        $this->status['code'] = $statusCode;
        $this->status['reason'] = ($reasonPhrase
            ? Constants::STATUS_CODES[$statusCode] : NULL);
        $this->setStatusCode();
        return $this;
    }
    ```

+   6.  Finally, we define a method that returns the reason for the HTTP status, which is a short text phrase, in this example, based on RFC 7231. Note the use of the PHP 7 null coalesce operator `??` that returns the first non-null item out of three possible choices:
    ```
    public function getReasonPhrase()
    {
        return $this->status['reason']
    ```