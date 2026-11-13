has only just been modified and requests a new copy of the page in full.

**Session Cache Control** When a PHP session is started, `no-cache` headers are automatically sent, along with the other HTTP headers that establish the session. You can use a different cache setting by using the `session_cache_limiter` function, with one of the values in Table 16.1 as an argument.