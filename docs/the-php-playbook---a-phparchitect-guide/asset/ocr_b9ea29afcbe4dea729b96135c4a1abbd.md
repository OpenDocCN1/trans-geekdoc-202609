```
// POST A MESSAGE TO TWITTER
public function tweet($message) {
    if(strlen($message) < 1) {
        return FALSE;
    }

    if ($this->already_tweeted($message)) {
        $this->done = TRUE;
    }

    // IF ONLY A TEST, JUST EMAIL THE INFORMATION - DO NOT TWEET
    if ($this->test) {
        $msg = '';
        if ($this->done) $msg .= "ALREADY DONE ";
        $msg .= "TWEET: $message";
        mail($this->you, 'What We Would Have Tweeted', $msg);
        return TRUE;
    }

    // DO NOT REPEAT YOURSELF
    if ($this->done) {
        return TRUE;
    }
    // STATUS UPDATE ON TWITTER
    $this->host .= "statuses/update.xml?status=".urlencode( stripslashes(
        urldecode($message))); curl_setopt($this-
        >ch, CURLOPT_URL, $this->host); $xxx
        = curl_exec($this->ch);
    $this->res = curl_getinfo($this->ch);
    if ($this->res['http_code'] == 0) {
        return TRUE;
    }
    if ($this->res['http_code'] == 200) {
        return TRUE;
    }
    return FALSE;
}
```

Great. Now we have added some consistency to our application, and removed any conditionals or loops that do not automatically have brackets. The next step is adding comments to our code so that we better understand its behavior and function.

There is a great amount of debate as to whether or not comments make a whole lot of sense. I think they help tremendously. If comments have not been written,