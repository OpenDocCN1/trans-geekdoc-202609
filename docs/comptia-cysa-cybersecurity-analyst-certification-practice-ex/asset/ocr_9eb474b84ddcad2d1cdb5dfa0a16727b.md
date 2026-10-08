# Command Prompt

```
TCP 127.0.0.1:50151 127.0.0.1:50152 ESTABLISHED 9708
TCP 127.0.0.1:50151 127.0.0.1:50151 ESTABLISHED 9708
TCP 127.0.0.1:50264 127.0.0.1:50265 ESTABLISHED 1652
TCP 127.0.0.1:50264 127.0.0.1:50265 ESTABLISHED 1652
TCP 127.127.127:127399 0.0.0.0 LISTENING 4
TCP 169.254.128:67139 0.0.0.0 LISTENING 4
TCP 169.254.128:67540 0.0.0.0 LISTENING 7588
TCP 192.168.240:24039 0.0.0.0 LISTENING 7588
TCP 192.168.240:49158 63.59.138:80 ESTABLISHED 1652
TCP 192.168.240:49164 162.125.183:143 ESTABLISHED 962
TCP 192.168.240:49176 162.125.183:143 ESTABLISHED 962
TCP 192.168.240:49245 131.253.74:436 ESTABLISHED 2840
TCP 192.168.240:49302 50.116.51:249 ESTABLISHED 5864
TCP 192.168.240:49918 63.59.138:80 ESTABLISHED 7248
TCP 192.168.240:49991 162.125.183:443 CLOSE_WAIT 962
TCP 192.168.240:49993 52.121.21:443 CLOSE_WAIT 962
TCP 192.168.240:50028 162.125.143:347 CLOSE_WAIT 962
TCP 192.168.240:50034 52.129.19:443 TIME_WAIT 0
TCP 192.168.240:50035 81.161.59,94:80 ESTABLISHED 9708
TCP 192.168.240:50043 53.197:80 TIME_WAIT 0
TCP 192.168.240:50054 172.27.21.126:443 ESTABLISHED 16640
TCP 192.168.240:50055 52.129.19:443 ESTABLISHED 1652
```

Figure 10-1 Outbound connections

| Name | PID | Status | User name |
| --- | --- | --- | --- |
| Dropbox.exe | 9612 | Running | admin |
| chrome.exe | 2840 | Running | admin |
| notepad.exe | 16640 | Running | admin |
| WINWORD.EXE | 3461 | Running | admin |

Figure 10-2 Running processes

+   - C is correct. There's little doubt that notepad.exe maintaining an outbound connection, on port 443 no less, is suspicious. That outbound communication should be investigated further.

+   - A, B, and D are incorrect. Dropbox and Chrome are expected to have outbound connections. Microsoft Word is not in the display of Figure 10-1, but it also might have an outbound connection.

+   9. The cybersecurity analyst hears of recent news about a new worm traveling through the company network, installing a bot that makes digital currency. Because