# Bash Scripting

## Resources

### Tutorials/ Getting Started

* [shellscript.sh](https://www.shellscript.sh/) "shell scripting tutorial"
* [Linux Documentation Project - Bash Guide for Beginners](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
* [BashGuide](http://mywiki.wooledge.org/BashGuide) "aid people interested in learning to work with BASH"
* [Serious Shell Programming](https://legacy.gitbook.com/book/freebsdfrau/serious-shell-programming/details)

### Reference

* [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/html_node/index.html)
* [Cheatsheet](https://devhints.io/bash) devhints.io
* [Bash Hackers Wiki](http://wiki.bash-hackers.org/)

### Tips & Tricks

* [Shell Scripts Matter](https://dev.to/thiht/shell-scripts-matter) "a summary of everything that can, and should be done when writing shell scripts."
* [ShellCheck](https://www.shellcheck.net/) "static analysis tool for shell scripts"
* [Unofficial Bash Strict Mode](http://redsymbol.net/articles/unofficial-bash-strict-mode/) "causes bash to behave in a way that makes many classes of subtle bugs impossible."
* [Google Shell Style Guide](https://google.github.io/styleguide/shell.xml)

### Talks

* [Introduction to Advanced Bash Usage](https://www.youtube.com/watch?v=uqHjc7hlqd0) by [James Pannacciulli](https://twitter.com/_jpnc)

## General Advice

### bash is not sh

While `bash` is "sh-compatible" some features of `bash` will break or cause unexpected behaviour in `sh`.

* Read [bash Is Not sh](https://rainbowhackerhorse.github.io/bash-Is-Not-sh/) for a more detailed explanation.

### Forget the .sh extension

Don't give scripts an `.sh` extension.

1. The [Google Shell Style Guide](https://google.github.io/styleguide/shell.xml) advises against it unless it's a library
2. It's a `bash` script, not an `sh` script

## Pipes

### grep

If you're piping to `grep` multiple times only the last `grep` in the sequence can be called with `-q`.

## Examples

### Shebang

First line of the script that indicates which interpreter is used to execute the file. The `#!` must be at the very start of the file, with no spaces or blank lines before it.

```text
#!/usr/bin/env bash
```

1. [Rational](https://stackoverflow.com/questions/21612980/why-is-usr-bin-env-bash-superior-to-bin-bash/21613044#21613044)
   * "`#!/usr/bin/env` searches `PATH` for `bash`, and `bash` is not always in `/bin`, particularly on non-Linux systems."
2. [Rational](https://stackoverflow.com/questions/16365130/the-difference-between-usr-bin-env-bash-and-usr-bin-bash/16365367#16365367)
   * "This way, you don't have to look for it in a specific place on the system, as those paths may be in different locations on different systems. As long as it's in your path, it will find it."

### Execute Script

Execute `bash` and tell it to read the script `myscript`. When executing the script this way the shebang line \(`#!`\) is just a comment, `bash` does nothing with it

```text
bash myscript
```

We can give the script executable permission. Instead of calling `bash` manually, we can execute `myscript` directly.

```text
chmod +x myscript  # Mark myscript as executable
./myscript  # Directly execute myscript
```

When `myscript` is executed this way, the shebang line \(`#!`\) is used to determine which interpreter to use.

### Debug Mode

Print every command before its execution, replacing the variables with their real values.

```text
set -x
```

[The Set Builtin](https://www.gnu.org/software/bash/manual/html_node/The-Set-Builtin.html)

### Unofficial Strict Mode

```text
set -euo pipefail
# -e: Exit if any command returns non-zero status code
# -u: Prevent using undefined variables
# -o pipefail: Force pipelines to fail on first non-zero status code
```

[Unofficial Bash Strict Mode](http://redsymbol.net/articles/unofficial-bash-strict-mode/)

