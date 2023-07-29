# Computer Science challenge - Regex tutorial!

This gist is a tutorial for a regex expression that matches a valid email address.

## Summary

This tutorial will cover a step-by-step deconstruction of a regex (regular expression) that matches a valid email address.

The regex expression that we will be decoding is ```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

Regular expressions are patterns used to match character combinations in strings. Refer to the components below  for this regex expression to match an email address.

### Anchors

Anchors match a position before or after characters.

 ^ – The caret anchor matches the beginning of the text.
 $ – The dollar anchor matches the end of the text.

In our example  ```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```, we have two anchors ^ and $, depicting where a matching pattern starts and ends.

The / slash located at the beginning /^ and ends at $/.

### Quantifiers

In our example  ```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```, we specify the number of instances of a character, group, or character class must be present in the string matched.

The left side of the @: ```/^([a-z0-9_\.-]+)```

We will match one string per the + sign before the last parentheses.

The right side of the @: ```([\da-z\.-]+)\.([a-z\.]{2,6})$/```

We will match one string as dictated by the + sign before the escaped period \.

```{2,6}``` --> matches between 2 and 6 of the preceding token (```[a-z\.]```)

### OR Operator

An OR operator | is for matching one of multiple patterns.

If we wanted to search an email string for "@" or ".com", we would use ```@|.com``` to confirm that an email has valid compenents to it.

### Character Classes

In our example  ```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```, we have [] square brackets, which are used to match different types of strings in order to match the desired search content. 

In this case let's divide the expression into two sections, before the "@" and after.

Left side of the @: ```[a-z0-9_\.-]+```

a-z --> matches lowercase character from a-z
0-9 --> matches any numerical character from 0-9
_ --> allow the usage of the underscore "_" in the matching.
\. --> escape character for the "." character.
+ --> We will match one string as dictated by the "+" sign before the last parentheses.
- --> allows the usage of "-" in the matching


Right side of the @: ```[\da-z\.-\.-]+)\.([a-z\.]{2,6})$/```

```\da-z\.-\.-]+)``` or before .com for matching.

\d --> matches any numerical character from 0-9
a-z --> matches any alphabetic character from a-z lowercase (case sensitive)
\. --> escape character for the "." character.
+ --> We will match one string as dictated by the "+" sign before the last parentheses.
- --> allows the usage of "-" in the matching

```\.([a-z\.]{2,6})$/``` or the .com scenarios for matching.

a-z --> matches any alphabetic character from a-z lowercase (case sensitive)
\. --> escape character for the "." character.
{2-6} --> matches between 2 and 6 (min 2 and max of 6) of the preceding token (```[a-z\.]```)
$ --> matched at the end of the string. It indicates that the ".com" or ".ca" has to be at the end of the email address string.

e.g (right of the @) --> @gmail.ca or hotmail.com


### Flags

A flag makes a regex search modify its behavior

A flag is denoted using a single lowercase alphabetic character.

An ```i``` flag for example, ignores all case-sensitive applications.

### Grouping and Capturing

In our example  ```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```, we have () parentheses used to group the two sections that generally make up a typical email address. That is before the "@" and after. 

That is to group two regular expressions. One will target before the @, and the other after to match the email address format.

### Bracket Expressions

In our example  ```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```, we use [] square brackets, which are used to match different types of strings in order to match the desired search content. 

### Greedy and Lazy Match

Greedy and Lazy match is a way to inform the regex expression as to how many characters are required for matching. In our example, we do not have a lazy method since we actually want the whole string. 

```/^([a-z0-9_\.-]+)``` -> We will match one character token or group.

### Boundaries

A boundary is denoted by a metacharacter ```\b```, and acts as an anchor similar to the ^ and $ sign.  

It is a zero-length match known as the "word boundary".

There are three different positions that qualify as word boundaries:

Before the first character in the string, if the first character is a word character.
After the last character in the string, if the last character is a word character.
Between two characters in the string, where one is a word character and the other is not a word character.

### Back-references

Backreferences match the same text as previously matched by a capturing group within a set of parentheses.

In our example: ```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```, we have ```[a-z0-9_\.-]+``` and ```[\da-z\.-]+``` as well as ```[a-z\.]{2,6}```.  This matches the user string before the "@" character and the email provider as well as the extension (.com, .org, etc).

This is useful if we want to match a pair of opening and closing HTML tags, as well as the text in between.

### Look-ahead and Look-behind

Look-ahead and look-behind, also known as “lookaround”, are zero-length assertions similar to the start and end of line, as well as the start and end of word anchors explained earlier. The difference is that lookaround actually matches characters, then simply returns the result: ```match``` or ```no match```. Hence the term: “assertions”. They do not consume characters in the string, but only assert whether a match is possible or not. Lookaround allows for the creation of regular expressions that are impossible to create without them, or that would get very longwinded without them.