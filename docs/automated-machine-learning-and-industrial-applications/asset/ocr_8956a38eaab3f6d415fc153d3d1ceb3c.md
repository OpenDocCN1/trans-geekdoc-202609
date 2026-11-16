# 11.7.2 Test Cases

Specifications and requirements, or what the app should be capable of, serve as the foundation around which test cases are constructed. Typically, descriptions of the program found elsewhere, such as specifications, requirements, and design parameters, serve as the basis for creating test cases. The majority of the tests conducted are functional in nature; however, sometimes, non-functional tests are used. Without knowing the underlying structure of the test object, the test designer chooses valid and invalid inputs and the proper output. Table 11.1 shows the test cases with different parameters.

# Table 11.1 Test cases.

| Test ID | Parameters | Expected output | Actual output | Status |
|---|---|---|---|---|
| TC1 | Capture high-resolution image of 500 rupee | Currency recognized as 500 rupee | Currency recognized as 500 rupee | PASS |
| TC2 | Capture low-quality image of 500 rupee with creases and fold | Currency recognized as 500 rupee | Currency recognized as 500 rupee | PASS |
| TC3 | Capture image of non-currency object (ex. floir) | Invalid input image | Invalid input image | PASS |
| TC4 | An image of Indian coin | Invalid input image | Invalid input image | PASS |