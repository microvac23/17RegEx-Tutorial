# How Validating a Password With Regex Works

Password validation is everywhere in any website that requires a login function. In this blog we will be discussing how a password is validated with regex. 
<br>Specifically a password with...
* A character length of at least 8
* One uppercase letter
* One lowercase letter
* and One number

## Summary

Here is the code snippet for a regex expression that satisfies the above criteria...

``` 
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[a-zA-Z\d]{8,}$ 
```

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
``` 
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[a-zA-Z\d]{8,}$ 
```
### Anchors

**^** is the beggining of the input being analyzed.
<br>**$** is the ending of the input being analyzed.
<br>So in our regex expression everything between those two characters are the qualifiers for the input.


### Quantifiers
**{n, m}** is a quantifier that looks for an expression with a character length between n and m. For example **{1, 7}** looks for an output with at least one and at most seven characters. However the max range parameter is optional, so just the first one is necessary.
<br> In our expression **{8,}** means we are looking for a password with at least 8 characters.


### Character Classes

**.*** is a character matching for any length of characters in an expression. Anything after a **.*** in regex is the qualifier it is searching for.<br> 

In our example **.*** is used multiple times. Let's take the first one... **(?=.*[a-z])**. In this one, following the **.*** is [a-z], so any lowercase letter. This validates there is at least one lowercase character in the whole of the expression.<br>

This leads to our next character class **[...]**. Any set of characters withing a pair of square brackets is used to specify which characters  to look for. In our example it is used three times... 
* [a-z] qualifies the expression for lowercase letters.
* [A-Z] qualifies the expression for uppercase letters.
* [a-zA-Z\d] states whole expression is comprised of lower and uppercase characters and numbers.
<br> 

**\d** is a character class which means a digit character. It is used two times in our regex expression. The first use, (?=.* **\d**), looks for any character that is a digit. The second use, [a-zA-Z **\d**], is saying the whole input is comprised of lowercase characters, uppercase characters, and **numbers**.

### Grouping and Capturing

**( )** is a grouping capture. It is used three times in our example regex expression. Each set of **()** containing the three character class inquriers...
* (?=.*[a-z]) look for any character that is lowercase.
* (?=.*[A-Z]) look for any character that is uppercase.
* (?=.*\d) look for any character that is a digit.


### Look-ahead and Look-behind

**?=** is the start of a look-ahead group. It matches what comes before it and compares whatever comes after it. 
<br>

In our example, it compares the beggining of the input , **^**, to the three character class inquiries discussed earlier...
* (?=.*[a-z]) look for any character that is lowercase.
* (?=.*[A-Z]) look for any character that is uppercase.
* (?=.*\d) look for any character that is a digit.

## Author

This article is written by Amadeus Machuca! 
<br>You can visit my GitHub profile here: [microvac23](https://github.com/microvac23)
