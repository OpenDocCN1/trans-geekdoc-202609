
In code using the MustCompile function looks roughly like the following code:

```
r := regexp.MustCompile(`pattern here...`)
```

## Box 12.10. What are those backticks?

When defining strings in Go, you will most often see people using double quotes (""). In addition to double quotes, you can also create strings using the backtick character (``).

The primary advantages of using the backtick is that you don't need to escape special characters, and your strings can have newlines in them that will be present in the string when you print it out without manually adding them.

They are often used when creating regular expressions because they use several special characters, and having to escape them can make the regular expression harder to read for developers.

The pattern we will be using when constructing our regular expression is shown below. Take a look at it, then we will take a few moments to explain broadly what it is.

```
^[a-z0-9._%+\-]+@[a-z0-9\-\.\+]+\.[a-z]{2,16}$
```

This is easiest to parse in pieces, so let's start with the first portion.

```
^[a-z0-9._%+\-]+
```

## 12.6. VALIDATING AND NORMALIZING EMAIL ADDRESSES

This portion of the pattern can be broken into two parts. The first is the ^ character, which states that this pattern must match the start of a string and can't match somewhere in the middle or end of a string.

After the ^ character we have the [] filled with some characters, and then followed by a plus sign (+). The letters in the brackets are a character set, which is a fancy way of saying we are going to define several different characters and our string can match any of them.

For example, if we were to use the regex pattern [a-z] we are saying this can match any single character between a and z, so any of the 26 lowercase letters in the English alphabet would match.

Our character set includes alphabet letters, digits (0–9), and a few special symbols (., _, %, and -). The last special symbol still needs to be escaped (the \ before escaping it) because the dash is a special symbol inside character sets that allows us to do ranges like a–z, but by escaping it we are telling our regular expression parser that we want to match the actual – character.

Whenever we create character sets, by default they will only match once. By adding the + sign after our character set we are stating that we can match any of those characters one or more times. That is, we are stating that it can repeat, but has to match at least once. Once we could match any of the following strings: "jon", "cat123", "d+o.g".

In short, this part of the regular expression is used to match all the letters that go before the sign. If you ever needed a new character in that part of an email address, you would update this portion of the regular expression.

Next is the @ part of the original regular expression.

```
^[a-z0-9._%+\-@[a-z0-9._\]+\.[a-z]{2,16}$$
      @
This part
```

Because this isn't wrapped in anything special, this simply states that we need

## CHAPTER 12. NORMALIZING AND VALIDATING DATA

match against the @ character exactly.

Everything we have so far states that our pattern must start at the beginning of a string, match 1 or more of the characters in our character set, and then be followed by a single @ character. So we would be matching things like “jon@

After we introduce another character set followed by a plus sign.

```
[a-z0-9.\-\]+
```

This character set is similar to the one we defined earlier, but is simpler. It only accepts letters, digits, dashes, periods, and the plus at the end signifies that we need to match this character set one or more times.

Note: We permit periods here that subdomains work in email addresses.

After that we have \. , which is an escaped period. When outside of a character set ([]), the period has a special meaning and will match any character, so if we want to match the period exactly we need to escape it with the backslash (\) character.

This line is like our @ sign we saw earlier - it states that we need to match against exactly one period.

Then we end our regular expression with the following:

```
[a-z](2,16)$
```

This states that we need a lowercase letter between a and z, and that we need between two and sixteen matches. After that the $ implies that this must match the end of the string, preventing us from matching on a string prefix.

We can be more specific in this part of our regular expression because every

## 12.6. VALIDATING AND NORMALIZING EMAIL ADDRESSES

valid top-level domain (TLD)$^8$ is between two and sixteen characters, long, and is composed of only alpha characters. While you might think that TLDs like .co..uk will fail this check, we don't need to worry about the .co portion because it will be matched earlier in our regular expression.

If this is all a little fuzzy still, don't worry. Regular expressions take a little while to get used to. What is important now is that you recognize that this will be used to match a pattern. Understanding how the regex was built isn't as important right now.

Again, this regular expressions is not perfect, but it covers our basic needs for now, and prepares us to start writing our validation function.

We are going to start by importing the regexp package.

```
import (
  "regexp"
  // ... Just add the import above
)
```

We are going to need to access our regular expression from userValidator methods, rather than creating a global variable we will use a field on that type.

```
type userValidator struct {
  UserDB
  hmac      hash.HMAC
  emailRegex *regexp.Regex
}
```

Before we can use the regular expression we need to compile and assign it to the field. We currently construct our userValidator inside the NewUserService function, but as our complexity starts to increase I like to break this into its own function. We can do that by creating a new userValidator, calling it from the NewUserService function much like we do with the userGorm.

> *https://en.wikipedia.org/wiki/Top-level_domain

## 398 CHAPTER 12. NORMALIZING AND VALIDATING DATA

```
func newUserValidator(udb UserDB,
hmac hash.HMAC) *userValidator {
 return &userValidator{
 UserDB: udb,
 hmac: hmac,
 emailRegex: regexp.MustCompile(`^[a-z0-9._%+\-]+@[a-z0-9._-]+\.[a-z]{2,16}$`),
}
}
```

```
func NewUserService(connectionInfo string) (UserService, error) {
ug, err := newUserGorm(connectionInfo)
if err != nil {
 return nil, err
}
hmac := hash.HMAC(secretKey)
uv := newUserValidator(ug, hmac)
return &UserService{
 UserDB: uv,
}
}
```

With all that prep done, we are ready to start writing our validation function. We will start by defining an error we return when email address doesn't appear to be valid. We can add this to the other errors we have in our variable block.

```
var {
ErrEmailInvalid is returned when an email address
does not match any of our requirements
ErrEmailInvalid = errors.New("email not valid")
}
```

After creating the error we can start writing the validation function. Since the regular expression is already created, all we need to do is use the MatchString method which will return true if a string matches our pattern.

> https://golang.org/pkg/regexp/#MatchString

## 12.6. VALIDATING AND NORMALIZING EMAIL ADDRESSES 399

```go
func (uv *Validator) emailFormat(user *User) error {
	if user.Email == "" {
		return nil
	}
	if !uv.emailRegex.MatchString(user.Email) {
		return ErrEmailInvalid
	}
	return nil
}
```

The "weird" part to this validation is the first block. If the email address is an empty string we skip this validation. Technically we don't need to do that, but I prefer to add this so that my validation can be used in situations where an email address is not required, and also because I have a validation that requires an email address which will catch this and return a more specific and helpful error.

Our last step is to add this validation to our Create and Update methods. You could also add it to the ByEmail method if you want, but the worst thing that will happen if we don't is an unnecessary query against the database that doesn't return any results, and I find that ErrNotFound returned in that case to be more useful for searching than the ErrEmailInvalid error.

```go
func (uv *Validator) Create(user *User) error {
	err := runUserValfns(user,
	uv.bcryptPassword,
	uv.setRememberUnset,
	uv.hmacRemember,
	uv.normalizeEmail,
	uv.emailFormat)
	// this is unchanged
}
```

```go
func (uv *Validator) Update(user *User) error {
	err := runUserValfns(user,
	uv.bcryptPassword,
	uv.hmacRemember,
	uv.normalizeEmail,
	uv.requireEmail)
```
