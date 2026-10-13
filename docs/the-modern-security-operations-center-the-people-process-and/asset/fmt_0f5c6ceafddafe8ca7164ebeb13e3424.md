
# Extensible Markup Language (XML)

Extensible Markup Language (XML) is a very popular method to use to format data. As its name implies, XML was designed to be extensible, meaning generic enough for a wide variety of applications. The look and feel of XML should make you think of a web page design, as that was XML’s original intent when created. XML is somewhat human readable and simple to create. A `< >` tag tells the operating system to open a section in XML and a `</>` tag represents to close a section. XML is a common way to encode data for APIs, which makes being able to read XML useful to IT pros looking to master automation.

The following code converts the plaintext file example I created for my daughter into the XML data format. Notice the list concept is represented in XML as `<tag>` to start the list and `</>` to end the list.

[Click here to view code image](Images/ch10_images.xhtml#p585pro01a)

```xml
<? xml version="1.0" encoding="UTF-8" ?>
   <books>
      <book bookID="1">
         <lead>Joey Muniz</lead>
         <title>The Modern Security Operations Center</title>
         <genre>Technology</genre>
         <desc>A technical journey to understanding a SOC</desc>
      </book>
   </books>
```

## JSON

JavaScript Object Notation (JSON) is a popular option for encoding API data. If you query a RESTful API using HTTP(S), the response you see will likely be in JSON format. Even though “JavaScript” is in the JSON name, JSON works with a wide variety of languages and applications. The format of JSON is different from XML but also is coded in a human-readable format. JSON heavily uses curly brackets (`{ }`) rather than the angle brackets (`< >`) used in XML, but the overall data structure is very similar to XML. JSON is also somewhat human readable and easy to understand and format.

The next bit of code is the same file example from the previous XML section but now formatted in JSON. Notice how the key value uses the `:` tag and lists are indicated in JSON by square brackets (`[ ]`).

[Click here to view code image](Images/ch10_images.xhtml#p586pro01a)

```json
{
   "books":{
      "book":[
      "author":"Joey Muniz",
      "title":"The Modern Security Operations Center",
      "genre":"Technology",
      "desc":"A technical journey to understanding a SOC",
      "_bookID":"1"
      ]
   }
}
```

## YAML

YAML (representing the recursive acronym YAML Ain’t Markup Language) is a much more human-friendly data serialization standard for all programming languages based on the makeup of bits and pieces of other languages. This means YAML can be used with other programming languages, typically with the purpose to write configuration files. YAML is a superset of JSON, meaning it can do everything JSON can do. To break down how YAML relates to other popular programming languages, YAML uses scalars, lists, and associative arrays based on how they are used in Perl. YAML uses the document separator `---`, which is also used in the Multipurpose Internet Mail Extensions (MIME) standard. YAML escape sequences are similar to C and whitespace wrapping is done exactly like you would do with HTML. Due to these overlapping characteristics with popular programming languages, YAML can be used with nearly any application that needs to transmit and store data.

The next bit of code is converting the previous XML and JSON example code into YAML.

[Click here to view code image](Images/ch10_images.xhtml#p587pro01a)

```yaml
---
- books:
      book:
- author:Joey Muniz
- title:The Modern Security Operations Center
- genre:Technology
- desc:A technical journey to understanding a SOC
- bookID:1
```

I’ll further explain YAML based on how it is used by Ansible, which is a tool covered later in the “Ansible” section. The first key concept to know about YAML is its core components. The contents of a YAML file define a single data structure that is composed of nested nodes, which means the whitespaces matter. The most common special characters in YAML you need to know are the following:

*   `:` Used between key/value pairs
*   `-` Denotes a sequence entry, meaning a list item
*   `#` starts a comment

> **Note**
>
> There are other special characters in YAML that you need to be aware of so that you don’t enter one incorrectly and cause YAML to fail to parse your data. See [https://www.tutorialspoint.com/yaml/yaml_syntax_characters.htm](https://www.tutorialspoint.com/yaml/yaml_syntax_characters.htm) for more information on YAML special characters.

The basic structure of a YAML file is a hash map, which is a data structure that implements an associative array (a structure that can map keys to values). An example of this hash map/key value system is mapping Jenny to the value 8675309. When I reference Jenny, I can abstract the value 8675309, making 8675309 a characteristic of Jenny. This concept applies to most data formats, including XML and JSON.

Much like other programming languages such as Python, YAML uses indentations to denote a change in scope level, which makes whitespaces significant. You can see a similar characteristic in the previous XML and JSON examples with a subset concept, such as the title of the book is indented with whitespace while the main topic (books) is not indented, allowing the understanding that the title is part of the book concept.

The following is a second YAML code snippet example that demonstrates these basic YAML programming concepts. Notice the `-` depicts a sequence entry, `:` is used between key values as well as to start the `do` statement, and `#` is used for comments to explain what each part of the code does.

[Click here to view code image](Images/ch10_images.xhtml#p588pro01a)

```yaml
#This program will divide one number by another
- divider:
    do:
      divide:
        - dividend: ${input1}
        - divisor: ${input2}
    publish:
      - answer: ${quotient} #Answer represents the result of the division
    navigate: [{ILLEGAL: FAILURE}, {SUCCESS: printer}]
```

Let’s look at a third example YAML file that can be run in Ansible to better understand YAML programming logic and see a more complicated YAML program. This YAML program represents a playbook that has two parts. The first part focuses on updating web servers, while the second part updates database servers.

[Click here to view code image](Images/ch10_images.xhtml#p588pro02a)

```yaml
---
- name: Update web servers
  hosts: webservers
  remote_user: root
 
  tasks:
  - name: Ensure apache is at the latest version
    ansible.builtin.yum:
      name: httpd
      state: latest
  - name: Write the apache config file
    ansible.builtin.template:
      src: /srv/httpd.j2
      dest: /etc/httpd.conf
 
- name: Update db servers
  hosts: databases
  remote_user: root
 
  tasks:
  - name: Ensure postgresql is at the latest version
    ansible.builtin.yum:
      name: postgresql
      state: latest
  - name: Ensure that postgresql is started
    ansible.builtin.service:
      name: postgresql
      state: started
```

Notice that `---` starts the program. The next part calls out variables, also known as hash maps. For example, when the `remote_user` info is referenced, the value of “root” is pulled. The tasks section tells the program what to do. Feel free to load this program into Ansible after I walk you through how to set up your Ansible environment later in this chapter.
