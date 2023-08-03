# Understanding Regexes, with Email Example

This gist is meant to serve as a tutorial for understanding the separate parts of a regular expression, or regex.

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

The particular regex that will be covered in this tutorial is displayed below.

/^([a-z0-9\_\.\-]+)@([\da-z\.\-]+)\.([a-z\.]{2,6})$/

This regex is meant to confirm that a given email address is valid. The different segments which make up the regex are outlined below, however this is the layman's explanation of the regex:

The / symbol at the beginnin and end is what identifies this as a regex. Starting from the beginning of the input, the text may contain any number of lowercase alphanumeric characters, underscores, or dashes, up until reaching an @ sign. After the @ sign, the text may again contain any lowercase alphanumeric characters or dashes, up until reaching a dot. After the dot, the text may contain any combination of lowercase letters and symbols that are between 2 and 6 characters long, and it will not evaluate beyond that.

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

### Anchors

The anchors commonly used in a regex are ^ and \$. These are positional characters, which are meant to judge where a given input is meant to be evaluated. ^ markes the beginning of the evaluation, and \$ marks the end.

The example regex contains both anchor tags.

### Quantifiers

Quantifiers are used to determine how many matches for an input the regex is looking for.

A \* means the input must match the regex criteria 0 or more times.
A + means the input must match the regex criteria 1 or more times.
A ? means the input can optionally include a specific criteria.
{} can also be used to quantify inputs. When given a single number, the regex will look for exactly that number of characters, When given two numbers, the regex will treat them as acceptable minimum and maximum numbers of characters.
{n}
{min, max}

As an example, the end of the email regex has {2,6}, meaning it will search for instances of between 2 and 6 characters.

### OR Operator

The OR operator, |, denotes that an input can have a number of choices for correct evaluation. For example, looking for an a, b, or c in the input would be evaluated as true with (a|b|c).

### Character Classes

Character classes are symbols that define different character sets, usually preceded by an escape character (\\).

\d will match with any numeric digit.
\w will match with any alphanumeric character, uppercase and lowercase.
\s matches with a whitespace character, including line breaks.

### Flags

Flags are symbols which go at the end of the regex, defining additional limits.

The letter 'g' will mark the regex as being global, finding as many matches in the input as possible. The letter 'i' will mark the regex as being case-insensitive, allowing for any character cases to match.

### Grouping and Capturing

Parenthesis are used to group together sets of characters, and to 'capture' them for usage later. For example, ([A-Z]{3}) would capture three alphanumeric capitals.

When using groups, the entire regex is considered 'Group 0'. Inside the regex, any additional groups inside of parenthesis are 'Group 1', 'Group 2', and so on.

These can be accessed later with either $ or l, followed by the number of the group desired. $ will allow to use the group in replacement syntax, while \ is used for referring to the group within the regex - for example, to find sets of repeating characters.

An example from the email regex is ([\da-z\.\-]+).

### Bracket Expressions

Characters inside of brackets are specific characters that the regex is looking for, similar to an AND operator. There are a few rules to be followed with bracket expressions.

If a - is used inside of brackets, it must be the first character, or else it will be treated as a range, such as A-Z which searches for any uppercase letter, or 0-9 which searches for any number.

^ is an exclusion symbol, and will note that the regex is NOT looking for specific characters.

Bracket expressions are also considered character classes.

An example from the given regex is [a-z0-9\_\.\-].

### Greedy and Lazy Match

Greedy matching, such as with the global flag, searches for any number of matching criteria no matter what lies in between. Lazy matching only finds as few occurrences of the criteria as possible.

A part of the regex can be made lazy by adding a ? after a quantifier, such as \*? or +?.

### Boundaries

A word boundary is an in-between marker, not denoting an actual character. The characters \b can be used to mark word boundaries in the criteria, or the space in between characters and whitespace.

### Back-references

Back-referencing allows a regex match to correct itself if it discovers partway through evaluation that a part of the input is incorrect. If part of an input is valid, but the matcher reaches an invalid character, then it will "backtrack" one character at a time until it has a proper match.

### Look-ahead and Look-behind

Collectively called look-around, this refers to the matcher's ability to match characters within specific boundaries - like the anchors - but then give up the result, returning only either match or no match. It only denotes whether a match is possible.

Lookahead can be either positive or negative, denoted as ?= and ?! respectively. w(?=a) will give a valid match to a w followed by an a. w(?!a) will return a valid match only if this is not the case.

Lookbehind can also be positive and negative, denoted as ?<= and ?<!. Therefore, one can use (?<=b)ee to search for 'ee' that is preceded by a b.

## Author

The author of this tutorial is AddisonNoxy on Github. They are currently a student in an online full-stack web development bootcamp, and developed this tutorial as part of the curriculum. Their github page can be found [here](https://github.com/AddisonNoxy).
