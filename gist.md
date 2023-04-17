# Computer Science Regex Tutorial

Regular Expression or regex for short, are a series of special characters that define a search pattern. In essense, regex can be used to find and/or replace a set of characters within a string. Since regex are a series of special characters, it can be universal and used within all programming languages.

## Summary

The regex I will be providing a tutorial for is:
<br />
![Screenshot of Email regex](https://gist.github.com/ItsMARPON/3de0eb86a1e2e3bbc75c401b539556e6/raw/dd0f5aaefc313c5fbcf08ec7c88db22f9091d6c0/email-regexex1.png)
<br />
This regex matches email addresses that is broken down into three groups. The first group signified by parenthesis `()`, may contain only lowercase letters, digits, underscores, dots, and hyphens before the `@` symbol. The second group may contain only lowercase letters, digits, dots, and hyphens after the @ symbol. In the last group, after the `\.` symbol, it may contain any lowercase letters or dots with further limiting the possible value of characters to a minimum and maximum of 2 and 6, respectively.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)


## Regex Components

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
<br />
A regex pattern must be wrapped in / slash characters.
<br />
![Screenshot of slash characters](https://gist.github.com/ItsMARPON/3de0eb86a1e2e3bbc75c401b539556e6/raw/46eff5e718148f88e236566bfbd32dc3dbd5c038/email-regex-wrap1.png)

### Anchors

![Screenshot of anchors](https://gist.github.com/ItsMARPON/3de0eb86a1e2e3bbc75c401b539556e6/raw/b2b2d914f1b44d9176b4d010b6ea990c78010856/email-regex-anchors1.png)

After wrapping the regex pattern in slash characters, the first components indicating the beginning and ending of a regex pattern are the anchors. In the email regex, the special characters `^` and `$` are both anchors. The `^` anchor is the very beginning of a string of characters. The `$` anchor is the ending of a string, with characters preceding it.

### Quantifiers

![Screenshot of quantifiers](https://gist.github.com/ItsMARPON/3de0eb86a1e2e3bbc75c401b539556e6/raw/b2b2d914f1b44d9176b4d010b6ea990c78010856/email-regex-quantifier1.png)

Quantifiers are greedy and can be made lazy. This means that Quantifiers can match as many occurences of particular pattern as possible by indicating the following symbols `*` and/or `+` and/or `?` and/or `{}` in the regex pattern.

In matching the email regex, in the first group `()`, the quantifier symbol `+` follows the bracket expression `[a-z0-9_\.-]` . The quantifer in this instance is to match the preceding character pattern one or more times. In the second group `()`, the quantifier symbol `+` follows `[\da-z\.-]` , meaning we want to match the preceding character pattern one or more times. In the third group, the quantifier symbol curly brackets `{}` indicate that we want to match `[a-z\.]` a minimum of two times and a maximum of 6 times. In other words, the quantifier `{2,6}` is setting the minimum and maximum number of times the combination of characters and/or symbols is to be matched.

### Character Classes

![Screenshot of Character Classes](https://gist.github.com/ItsMARPON/3de0eb86a1e2e3bbc75c401b539556e6/raw/b2b2d914f1b44d9176b4d010b6ea990c78010856/email-regex-charClass1.png)
<br />
A Character Class also called Character set, are indicated by square brackets `[]`. When using square brackets, one or more characters or special characters are placed inbetween the brackets. It expresses the pattern of any characters or special characters within the square bracket, and is known as bracket expression or positive character group. It is important to note that if we are trying to match special characters, the placement of special characters (symbols) within the square brackets matter. When trying to match the symbol characters in a regex pattern, it must come after the alphanumeric characters within the square brackets. If the special characters are at the beginning or middle of the character class set, then it has a different meaning. For example, if the hyphen is placed between two alphanumeric characters like `[a-m]`, it is no longer the literal symbol. It changes to mean a range of characters. In this case, the string can contain any lowercase character between the range of letters a through m.

In matching the email regex, there are three character classes. The character classes are `[a-z0-9_\.-]` and `[\da-z\.-]` and last but not least, `[a-z\.]` . These will be further explained in the Bracket Expression section.

### Grouping and Capturing

![Screenshot of Grouping constructs](https://gist.github.com/ItsMARPON/3de0eb86a1e2e3bbc75c401b539556e6/raw/b2b2d914f1b44d9176b4d010b6ea990c78010856/email-regex-group1.png)
<br />
The Grouping construct is indicated by parentheses `()` and each section within the parenthesis is known as a subexpression. In order, to check multiple parts of a string to determine if different sections meet different requirements, then grouping constructs are necessary to accomplish this task. Subexpressions will look for an exact match.

Grouping constructs have two categories, capturing or non-capturing. A grouping construct that is capturing will capture the matched character sequence and store it in memory for possible use at a later time. A grouping construct that is non-capturing will not capture and store the matched character sequence, so it does not utilize any memory storage. It is indicated by adding `?:` at the beginning of the subexpression within the parenthesis.

Each capturing group construct treats the regex pattern inside the parenthesis as a subgroup or unit. This can be later extracted and used from all sorts of data. There can be as many groups needed and it is numbered by counting their opening parenthesis from left to right.

For example, `(dog)|(cat)` consists of two grouping constructs. The first subexpression `(dog)` is looking for a part of the string that matches the string "dog" exactly. The second subexpression `(cat)` is looking for a part of the string that matches the string "cat" exactly. In between the two subexpression is the pipe symbol | which means to match the regular expression preceding it or the regular expression following it. The regex match will either "dog" or "cat" in the string.

In the email regex, there are three grouping constructs as highlighted in the image above. Each grouping construct contains character class [] and Quantifiers which will be further explained in the Character Classes, Bracket Expressions, and Quantifiers sections.

### Bracket Expressions

![Screenshot of Bracket Expression](https://gist.github.com/ItsMARPON/3de0eb86a1e2e3bbc75c401b539556e6/raw/b2b2d914f1b44d9176b4d010b6ea990c78010856/email-regex-bracketexpr1.png)
<br />
A Bracket Expression is when the character class `[]` contains alphanumeric characters or special character symbols inbetween the brackets. It expresses the character pattern that is required for the string. Essentially, characters can be in any order and the string can contain any of these combinations.

In matching the email regex, there are three bracket expressions (character sets) within the regex. The first bracket expression `[a-z0-9_\.-]` means any lowercase letter character between the alphabet range of a through z, or any number range of 0 through 9, or the symbols underscore  `_` or literal dot `.` or hyphen `-` can be in the string.

In the second bracket expression `[\da-z\.-]` , means any digit range or letter character between the alphabet range of a through z, or literal dot . or hyphen can be in the string.

In the third bracket expression `[a-z\.]` , means any letter character between the alphabet range of a through z or literal dot `.` can be in the string.


### Greedy and Lazy Match

As mentioned in the Quantifiers section, quantifiers can be greedy or lazy. In the email regex, the quantifier is greedy, meaning it will match as many occurrences of the pattern as possible. It will match the pattern at least one or more times. In the first bracket expression `[a-z0-9_\.-]+` , The first pattern character can be any lowercase alphanumeric or symbol underscore, dot, or hyphen. Once it matches one of these characters in the bracket expression, then due to the symbol `+`, it tries to find a match one or more times in the string. It adds to match one character after another until it arrives at the `@` symbol. 

In the second bracket expression `[\da-z\.-]+` , the first pattern character after the `@` symbol, can be any lowercase alphanumeric or symbol dot or hyphen. Once it matches one of these characters, then it tries to find a match in the rest of the string one or more times until it arrives at the final literal dot symbol in the domain extension.

The third bracket expression `[a-z\.]{2,6}` , the first pattern character after the final literal dot symbol, can be any lowercase alphabet character or literal dot symbol. Once it matches one of these characters, then it tries to find a match in the rest of the string between 2 to 6 lowercase letters or dots in length. 

### Boundaries

The Boundaries are like the anchors mentioned above. The boundaries are important if we want to match a particular position in the string. This adds a more precise pattern to match by specifying the pattern with boundary markers.

In the email regex, we have the boundaries `^` and `$` that anchor the regex pattern to the beginning of a string and the end of a string, respectively.


## Author
Currently, I am enrolled in the University of Minnesota Full-Stack Web Development program. I have a background in Finance and Accounting and hope to bring my background into a new endeavor starting with web developement.

Contact me with questions at the following links:
<br />
GitHub User Name: itsMARPON
<br />
GitHub URL: https://github.com/ItsMARPON
<br />
Email: itsmaryyang@gmail.com
