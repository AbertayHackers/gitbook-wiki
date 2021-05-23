---
description: >-
  An introduction to Markdown, the basic markup language for online text formatting
---

# Markdown

*Written by [Isaac](../../members/isaac.md)*

Markdown is an extremely lightweight markup language for formatting text in a plaintext editor. Places Markdown is used include Wikipedia's editor, GitHub (for documentation and readme files), online forums, blogs, Discord, and this wiki!

The specification for the language was outlined in [this](https://daringfireball.net/projects/markdown/) blog post by John Gruber, however due to some ambiguities, there are a few different implementations that do certain things differently. The description in this article will give a basic overview of the language and aim to point out posible differences when they arise

## Paragraphs

Paragraphs are perhaps the simplest thing to describe in markdown, to make one, simply type as normal:

```markdown
This is a paragraph

This is another paragraph

Don't forget to leave a blank line between paragraphs for a line break!
```

## Headings

To create headings, simply add hash(es) (#) in front of a word or phrase.

[^1]: Make sure to add a space after the hash, this is best practise and makes it easier for someone to read the markdown itself

The number of hashes you add should correspond to the level of headings you want to use. so for example:

```markdown
# This would be heading level 1
## This would be heading level 2
### This would be heading level 3
```

And so on. These headings (as with a lot of Markdown's syntax) have a direct equivalent in HTML, the markup language that webpages use for formatting. The equivalent would be using the \<h1>, \<h2>, and \<h3> tags respectively

### Alternate Syntax

For headings 1 and 2 there is alternate syntax. This involves placing a number of equals signs (=), and  dashes (-) following the text you wish to be in heading levels 1 and 2 respectively, this looks like this:

```markdown
Heading Level 1
===============

Heading Level 2
---------------
```

## Emphasis, Quotation, and Strikethrough

### Italic

Italic text can be generated in two main ways, these ways are using asterisks (\*), and underscores (\_). "*This text is in Italics*, and _so is this text_", would be written like so:

```markdown
*This text is in Italics*, and _so is this text_
```

If you must emphasise only part of a single word, stick to using asterisks, as different implementations of Markdown disagree on how to handle underscores mid-string.

### Bold

Bold text is created by adding two asterisks or two underscores instead of just one. "**This text is bold**, and __so is this text__" would be written like:

```markdown
**This text is bold**, and __so is this text__
```

### Block Quotes

To make a blockquote, simply add a \> in front of a paragraph:

> like so

You can also create nested blockquotes using multiple \>s 

> this 
> > looks
> > > like
> > >
> > > > this

Or in code:

```markdown
> this 
> > looks
> > > like
> > > > this
```


### Strikethrough

You can strikethrough text (make it look like someone has crossed it out with a ruler) using two tilde (\~) characters either side of the text in question, ~~like this~~ 

```markdown
and ~~like this~~
```

### Mixing

It is possible in Markdown to mix different forms of emphasis, for example you can have a bold italic strikthrough-ed piece of text, which would look 

> ~~***like this***~~ 

after the markdown is comipled, and like this in text editor:

```markdown
> ~~***like this***~~
```

## Lists

In Markdown (and most other markup languages), there are two kinds of list, an ordered (or numbered) list, and an unordered list, which is usually referred to as bullet pointed or something to that effect. 

### Ordered Lists

To make an ordered or numbered list, simply start a new line with the number 1 followed by a full stop (like "1."), it actually doesn't matter what the rest of the numbers are 9they don't even have to be in order!) as long as they're numbers followed by a full stop.

1. Here
2. Is
3. An
4. Ordered
5. List

When indenting an ordered list, it's typically best to begin the new indent with the number 1 again

1. This
2. Is
3. Another
   1. Ordered 
   2. List
      1. But
      2. With
      3. Indents
   3.  For
   4. Some
4. Extra
5. Spice. 

### Unordered Lists

Unordered lists can be made in a number of ways, but they will usually always compile into the same format (normally bullet points or dashes). To create an unordered list you can use one of three characters, the dash (\-), the asterisk (\*), or the plus (\+) in front of line items. Like so:

- This
- One
- Uses
- Dashes

* This
* One
* Uses 
* Asterisks

+ This
+ One
+ Uses
+ Pluses

## Links and Images

Links and images are actually added in very similar ways. A plain hyperlink can be added by simply copy-pasting it into the text, like so: https://www.youtube.com/watch?v=dQw4w9WgXcQ. If you want to add a bit of text to the link you can do it by putting a set of square brackets (\[\]) around the text, and a set of normal brackets (\(\)) around the link, this ends up [compiling like this](https://www.youtube.com/watch?v=dQw4w9WgXcQ), but looking like this in the text editor:

```markdown
[compiling like this](https://www.youtube.com/watch?v=dQw4w9WgXcQ)
```

Images are formatted in the exact same way, but with an exclamation point (\!) in front of the first square bracket. You can (and indeed always should) place image alt text where you would have placed the link's text, for example:

![What a handsome young lad, I sure hope he never lets me down!](https://www.nme.com/wp-content/uploads/2017/07/RICK_ROLL.jpg)

This ends up looking like this in text editor:

```markdown
![What a handsome young lad, I sure hope he never lets me down!](https://www.nme.com/wp-content/uploads/2017/07/RICK_ROLL.jpg)
```

## Code

Sometimes it's important to embed a snippet or two of code in your markdown. When this happens you have two options, one for a single line of code, and one for a block.

For a single line of code, envelop it in a set of backticks (found next to the 1 on the keyboard). `print("like this")`.

For a whole block of code, use three backticks in a row, followed by the file extension or name of the language that you're using (this is done to highlight syntax)

```c++
#include <iostream>

int main() {
    std::cout << "This is how you do it in c++";
    return 0;
}
```

Together, they look look like this in the code editor:

```markdown
`print("like this")`

(backticks here)c++
#include <iostream>

int main() {
    std::cout << "This is how you do it in c++";
    return 0;
}
(backticks here)
```

## Escaping Characters

To "Escape" characters, or make special characters (such as \*, \>, \`, etc.) print, you simply add a backslash (\\) to the front of whatever character you're wanting to escape, in the text editor it looks like this:

```markdown
\* asterisks everywhere!!! \*
```
