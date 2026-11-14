authentication, and cumbersome security configuration, as you will see later in this chapter.

# Shodan IoT Search Engine

The Shodan search engine is focused on Internet-connected devices15 and is slowly becoming known as the Internet of Things (IoT). It is important to realize that this is not your father’s Google. Shodan searches for banners, not web pages. In particular, Shodan scans the Internet looking for banners it recognizes and then indexes that data. You can submit your own banner fingerprints and IPs for scanning, but that requires a paid license.

# Web Interface

If you want to lose an afternoon, or even weekend, simply go to https://images.shodan.io (requires $49/year membership). Perhaps you will find a large toddler, napping, as shown next. (That’s a joke; this is obviously a tired adult.)

```
554 RTSP/1.0 200 OK
tcp CSeq: 1
rtsp-tcp Server: Hipcam RealServer/V1.0
Public: OPTIONS,DESCRIBE,SETUP,TEARDOWN,PLAY,SET_PARAMETER,GET_PARAMETER
```

![](bbox=[0.123, 0.479, 0.877, 0.808])

On a more serious note, with a little more searching, using the search string “authentication disabled” and filtering on VNC, you’ll receive more interesting results (notice the “Motor Stop” button).