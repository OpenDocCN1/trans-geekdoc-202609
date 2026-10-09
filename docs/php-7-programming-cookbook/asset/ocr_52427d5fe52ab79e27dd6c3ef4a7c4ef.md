# 12

# Improving Web Security

In this chapter, we will cover the following topics:

+   - Filtering `$_POST` data
- Validating `$_POST` data
- Safeguarding the PHP session
- Securing forms with a token
- Building a secure password generator
- Safeguarding forms with a CAPTCHA
- Encrypting/decrypting without `mcrypt`

# Introduction

In this chapter, we will show you how to set up a simple yet effective mechanism for filtering and validating a block of post data. Then, we will cover how to protect your PHP sessions from potential session hijacking and other forms of attack. The next recipe shows how to protect forms from **Cross Site Request Forgery (CSRF)** attacks using a randomly generated token.
The recipe on password generation shows you how to incorporate PHP 7 true randomization to generate secure passwords. We then show you two forms of **CAPTCHA**: one that is text based, the other using a distorted image. Finally, there is a recipe that covers strong encryption without using the discredited and soon-to-be-deprecated `mcrypt` extension.