# AWK

### Intro

AWK is a very powerful interpreted programming language capable of advanced data manipulation. There are 3 versions:

- **AWK** - Original version from AT&T Labs
- **GAWK** - GNU AWK. All Linux distros ship with this - it is fully compatible with AWK and NAWK
- **NAWK** - Newer Awk. Updated version from AT&T

### Basic Usage

#### **WIP**

The basic usage for awk in Linux is:

```bash
awk '{[commands]}' [input file]
```

The 'commands' section can include any combination of instructions available in the AWK programming language and must be enclosed in apostrophes (').

### Variables

Variables in AWK are referenced with a $ sign. A number of variables are defined by the interpreter when an input file is provided. The most useful of these store parts of the line currently in use:

- $0 - Content of the whole line currently in use. If matching a pattern, this will be the entire line which contains the matching text
- $1, $2, $3 etc. - The current line is split up into sections using the **delimiter value (add reference)** which by default is the space character. Thus if a delimiter is not specified these variables will store the 1st, 2nd, 3rd… column of the line.

### Pattern Matching

AWK has full support for [regex](https://wiki.hacksoc.co.uk/guides/regex), and will match lines based on the pattern provided. For example

```awk
awk '/hello/ {print $0}'
```

will print every line in the file which contains the string 'hello' (note the '/' characters wrapping the text to match - these are required by the interpreter). Any regex can be used in this context.

Any commands included within the '{}' characters will be performed on the line matching the pattern. If there are multiple matches, AWK will step through each match and perform these instructions on each line in turn. Multiple commands can be included here, separated by a semi-colon (e.g. ''awk '/test {$output=$1+“ ”).