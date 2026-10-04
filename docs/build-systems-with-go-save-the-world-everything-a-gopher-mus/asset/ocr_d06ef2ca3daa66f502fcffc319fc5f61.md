# CHAPTER 10 TEMPLATES

While you read these lines, there are thousands of millions of reports, web pages and other structured and non-structured data collections being generated. Many of them share a common template that is filled with information extracted from users and processed accordingly to a pre-defined logic. For example, the email sent to your account to reset your forgotten password is always the same, except for small chunks containing data you should be aware of.

From a practical perspective, these templates should be easy to change and modify without necessarily requiring to modify any source code. Go provides data-driven templates for generating textual output. These templates are executed by applying data structures that contain the data to be represented in the template package. This Chapter explores how to use these templates using the text/template and html/template packages for text and HTML respectively.

# 10.1 FILLING WITH STRUCTS

The text/template22 package defines the syntax to generate textual templates. Our goal is to fill the gaps of a template with incoming data. Let's consider the string below.

> Dear {{.Name}}
You were registered with id {{.UserId}}
and e-mail {{.Email}}

This defines a template that is expected to be filled with a struct with fields Name, UserId, and Email. Example 10.1 uses this syntax in conjunction with a User type to generate personalized messages.

# 10.1: Fill template with a struct.

```
package main

import (
	"text/template"
	"os"
)

type User struct{
	Name string
	UserId string
	Email string
}

const Msg = 'Dear {{.Name}}.\nYou were registered with id {{.UserId}}.\nand e-mail {{.Email}}'.
```

![](bbox=[0.703, 0.646, 0.879, 0.725])