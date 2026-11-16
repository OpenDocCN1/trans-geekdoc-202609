# # Table 11.1 Test cases. (Continued)

| Test ID | Parameters | Expected output | Actual output | Status |
|---|---|---|---|---|
| TC5 | A blurred image of 500 rupee note | Currency recognized as500 rupee | Currency recognized as 500 rupee | PASS |
| TC6 | A rotated image of a 10 rupee note | Currency recognized as 10 rupee | Currency recognized as 10 rupee | PASS |
| TC7 | A severely damaged currency note with missing corners | Unable to recognize due to extreme damage | As expected | PASS |
| TC8 | Capture high-resolution image of 500 rupee | If it is real, able to recognize the characters on the image | As expected | PASS |
| TC9 | Capture low-quality image of 500 rupee with creases and fold | If it is real, able to recognize the characters on the image | As expected | PASS |
| TC10 | A blurred image of 500 rupee note | If it is real, unable to detect all the characters on the currency note | As expected | PASS |