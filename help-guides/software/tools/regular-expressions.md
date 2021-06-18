# Regular Expressions

## Intro

In theoretical computer science, a regular expression is a sequence of characters that define a _search pattern_. It's basically a fancy way of doing text searches. Very useful in combination with sed and [awk](https://wiki.hacksoc.co.uk/guides/linux/awk)![xkcd 208 - Regular Expressions](../../../.gitbook/assets/regular_expressions.png)

## Basic Usage

If you wanted to search through a long file looking for email addresses you might do something like

```text
grep -E “[a-z]+@[a-z]+\.(com|org)” file.txt
```

That looks like someone's mashed their face on the keyboard so lets break it down into separate components to make it easier to understand.

`[a-z]` matches anything inside the square brackets exactly once \(in this case, it's looking for any lowercase letter\)

`+` this means the preceding element gets matched one or more times \(so multiple letters\)

`@` matches the character found in the middle of an email address

`[a-z]+` same again, a sequence of one or more lowercase characters

`\.` this tells it to use the actual `.` character instead of using it as a metacharacter

`(com|org)` the brackets get interpreted as a subexpression. in this case 'com' or 'org

This is obviously just an example to show you some features of regex. An [RFC 822 compliant regex](http://stackoverflow.com/questions/201323/using-a-regular-expression-to-validate-an-email-address) is unreadable. In practice I'd probably just do \w+@\w+.\w \(word@word.word\)

## BRE vs ERE

This tutorial assumes you're using ERE \(Extended Regular Expressions\). Basic, or BRE, is just the same but you have to backslash brackets and you can't use `?`,`+` or `|`. That's also why we used `grep -E` instead of `grep -e`

## List of Metacharacters

| **Metacharacter** | **Description** |
| :--- | :--- |
| `.` | Matches any single character \(whether this includes newlines sometimes depends on the application\) |
| `[ ]` | A bracket expression. Matches a single character that is contained within the brackets. For example, \[abc\] matches “a”, “b”, or “c”. \[a-z\] specifies a range which matches any lowercase letter from “a” to “z”. |
| `[^ ]` | Matches a single character that is not contained within the brackets. For example, `[^abc]` matches any character other than “a”, “b”, or “c”. `[^a-z]` matches any single character that is not a lowercase letter from “a” to “z”. |
| `^` | Matches the starting position within the string. In line-based tools, it matches the starting position of any line. |
| `$` | Matches the ending position of the string or the position just before a string-ending newline. In line-based tools, it matches the ending position of any line. |
| `( )` | Defines a marked subexpression. The string that gets matched in the parentheses can be recalled later but that's a bit more advanced. |
| `\|` | The choice \(also known as alternation or set union\) operator matches either the expression before or the expression after the operator. For example, `abc \| def` matches “abc” or “def”. |
| `*` | Matches the preceding element zero or more times. For example, `ab*c` matches “ac”, “abc”, “abbbc”, etc. `[xyz]*` matches “”, “x”, “y”, “z”, “zx”, “zyx”, “xyzzy”, and so on. `(ab)*` matches “”, “ab”, “abab”, “ababab”, and so on. |
| `?` | Matches the preceding element zero or one time. For example, ab?c matches only “ac” or “abc”. |
| `+` | Matches the preceding element one or more times. For example, ab+c matches “abc”, “abbc”, “abbbc”, and so on, but not “ac”. |
| `{m,n}` | Matches the preceding element at least `m` and not more than `n` times. For example, `a{3,5}` matches only “aaa”, “aaaa”, and “aaaaa”. This is not found in a few older instances of regexes. |

## More Examples

`.at` matches any three-character string ending with “at”, including “hat”, “cat”, and “bat”.

`[hc]at` matches “hat” and “cat”.

`[^b]at` matches all strings matched by `.at` except “bat”.

`[^hc]at` matches all strings matched by `.at` other than “hat” and “cat”.

`^[hc]at` matches “hat” and “cat”, but only at the beginning of the string or line.

`[hc]at$` matches “hat” and “cat”, but only at the end of the string or line.

`\[.\]` matches any single character surrounded by “\[” and “\]” since the brackets are escaped, for example: “\[a\]” and “\[b\]”.

`s.*` matches s followed by zero or more characters, for example: “s” and “saw” and “seed”.

`[hc]+at` matches “hat”, “cat”, “hhat”, “chat”, “hcat”, “cchchat”, and so on, but not “at”.

`[hc]?at` matches “hat”, “cat”, and “at”.

`[hc]*at` matches “hat”, “cat”, “hhat”, “chat”, “hcat”, “cchchat”, “at”, and so on.

`cat|dog` matches “cat” or “dog”.

## Further Reading

[Wikipedia](https://en.wikipedia.org/wiki/Regular_expression)

[regex debugger](https://regex101.com/)

[more visual debugger](https://www.debuggex.com/)

[crossword to test your skills](https://regexcrossword.com/)

[more advanced puzzles](http://regex.alf.nu/)

[Regexlib](http://regexlib.com/Search.aspx) - if you don't want to reinvent the wheel

