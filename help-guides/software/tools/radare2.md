---
description: a walkthrough and usage guide for the Radare2 reverse engineering framework
---

# Radare2

_By_ [_Isaac_](../../../members/members/isaac.md)

![The Radare2 Logo](.gitbook\assets\r2logo.png)

## What is it?

Radare2 is a framework for performing reverse engineering and binary analysis both statically (when the program isn't running) and dynamically (when it is running). R2 is made up of a number of smaller command line utilities, including, but not limited to, the following:

1. `Radare2` - The core tool, a hex editor and debugger, also allows for other tools to be pulled and used seamlessly to perform actions such as data analysis, string extraction, disassembly, binary patching, data comparison, searching, writing, visualising, and has functionality for scripting in Python and JavaScript, amongst others.
2. `Rabin2` - Extracts info from executable binaries such as ELF and PE data, which is metadata for Linux and Windows files.
3. `Rasm2` - Assembler and disassembler for x86, x86-64, ARM, and a slew of other architectures.
4. `Rahash2` - A hash tool
5. `Radiff2` - A tool that allows the user to see the differences between two files 

Using Radare2 is as simple as writing `r2 path/to/file` on the command line, once in, you're presented with a prompt that reads out the location of the entry point of a program in hexadecimal. In the case of `/bin/ls` that entry point is `0x000067d0`. After this, its simply a case of learning the tool. Radare2 is similar to [Vim](help-guides\software\tools\vim.md) in a few ways, not least the high skill ceiling and steep learning curve. However where it is arguably most similar is how similar learning it feels to learning a language, due to the fact that both tools make use of compound mnemonics to perform actions. For example, in Vim, using `ci)` will delete anything inside a set of parentheses and put you in edit mode to change the contents. In the same way, using something like `pdf` will disassemble functions, which you can learn by knowing that `p` prints, `pd` prints disassembly, and `pdf` prints disassembled functions.

To learn these commands, or if a user needs a reminder of them, said user can add a `?` symbol to the end of a command, using the print disassembly example, `pd?` prints the following:

```
[0x000067d0]> pd?
Usage: p[dD][ajbrfils] [[-]len]   # Print N bytes/instructions bw/forward
| NOTE: len        parameter can be negative
| NOTE:            Pressing ENTER on empty command will repeat last print command in next page
| pD N             disassemble N bytes
| pd -N            disassemble N instructions backwards
| pd N             disassemble N instructions
| pd--[n]          context disassembly of N instructions
| pda[?]           disassemble all possible opcodes (byte per byte)
| pdb[?]           disassemble basic block
| pdc[?][c]        pseudo disassembler output in C-like syntax
| pdC              show comments found in N instructions
| pde[q|qq|j] [N]  disassemble N instructions following execution flow from current PC
| pdo[N]           convert esil expressions of N instructions to C (bytes for pdO)
| pdf[?]           disassemble function
| pdi              like 'pi', with offset and bytes
| pdj              disassemble to json
| pdJ              formatted disassembly like pd as json
| pdk[?]           disassemble all methods of a class
| pdl              show instruction sizes
| pdp[?]           disassemble by following pointers to read ropchains
| pdr[?]           recursive disassemble across the function graph
| pdr.             recursive disassemble across the function graph (from current basic block)
| pdR              recursive disassemble block size bytes without analyzing functions
| pds[?]           disassemble summary (strings, calls, jumps, refs) (see pdsf and pdfs)
| pdu[aceios?]     disassemble instructions until condition
| pd, [n] [query]  disassemble N instructions in a table (see dtd for debug traces)
| pdx [hex]        alias for pad or pix

```

## Installation

Linux users can install Radare2 either through their package manager, e.g. `sudo apt install radare2` for debian-based systems, or perhaps the more recommended approach, cloning directly from the github repository by running the following commands in succession:

```sh
git clone https://github.com/radareorg/radare2.git;
cd radare2;
sys/install.sh;
```

And to update, simply run `git pull` in the source tree.

## Usage

### Command line Options

As mentioned previously, Radare2's standard usage on the command line is `r2 /path/to/file`, naturally, however, there are flags you can use on the command line to enhance the behaviour of the program from the start. A couple of the most useful commands are listed below:

```
-A              run 'aaa' command (analysis of all referenced code in a binary)
-c 'cmd...'     run arbitrary commands in radare without having to open first
-d              debug executable
-h or -hh       show help
-w              open file in write mode
```

### Radare2 Commands

- `iS`: List sections in an executable
- `px @ [memory address]`: print hexdump at memory address
- `ps @ [memory address]`: print string at memory address
- `ws "Hello World!" @ [memory address]`: overwrite things in memory location (default will not allow overwriting on disk until commit)
- `fo`: print a quirky message (a fortune),same that you get shown at launch
- `?E "Hello World!"`: display a message from Clippy!
- `?E [backtick]fo[backtick]`: surround a command in backticks to pipe it to another command (this shows a fortune in Clippy)
- `s [memory address] OR s [memory address]+0x24`: to navigate (seek) to an address, can do maths in the seek too
- `afl`: list functions inside the program/exe (with descriptors)
- `pdf [function name]`: Print the disassembly of a function, `pd n` will also print `n` instructions
- `pdd`: decompile a function with built in decompiler (you can see code lol)
- `pdg`: decompile function with Ghidra decompiler (looks nicer lmao)
- `? [number]`: quickly convert between data types, also supports maths
- `![command]`: run system commands from Radare2
- `axt [function name]`: see all the places a function is called (cross references)
- `agCd`: view and manoeuvre the control flow graph of a function - may be important for malware reversing for me
- `iz`: print out all the strings
- `pdf~edi`: Search command output using `~`, `~+` is case insensitive (like grep), example prints disassembly of a function and searches for the keyword "edi"
- `aa OR aaa`: analyse the program
- `aaaaaaa`: call in tech support lol 
- `eco`: list and configure themes 
- `eco gruvbox; pd 5`: chain commands via `;`, example switches theme to gruvbox and then prints 5 lines of disassembly at the current memory location
- `V or V!`: enter visual or visual panels mode 
- `(in visual panel mode) r2048`: possible to play 2048 using visual panels mode menu
- `itj`: get command outputs as JSON, `it` command gets hashes
- `itj~{}`: pretty print formatted JSON 
- `itj~{}md5`: access JSON elements you want to parse out 
- `(in python) imprt r2pipe`: script analysis via r2pipe 
- `ii`: gets list of imported functions 
- `afl?`: print help for a command with `?`
- `afl[TAB]`: or just hit tab for same effect 
- `pqz`: print data as a qr code via `pq`, `pqz` prints based on current string, `pq20` prints next 20 bites as QR
- `(in visual mode) (`: get festive with snow mode
- `pa mov x19, x1`: convert mnemonics into hex pairs using `pa`
- `pad`: reverses `pa`
- `CC Hello World! @ [memory address]`: add comments 
- `CC-`: remove comments
- `afn [new function name] @ [old function name]`: rename things to make it easier to understand
- `pdga`: print disassembly and ghidra decompile side by side to help understand assembly
- `/R`: list ROP gadgets available in the program
- `(in cli) r2 -i example.r2s -e scr.interctive=false -e cfg.slides.heading.colour=yellow`: write and present slides in r2, write in markdown
- `[backticks in slides]`: write r2 commands in slides and run them live
- `(in cli) r2 -d [program]`: debug programs 
- `db, dc, dr`: set breakpoint, continue program, print registers
- `pd @ rdi`: dump registers and stack
- `pdf @ [function name]`: leverage temporary seeks to avoid repeated jumping around
- `pd 2 @@ [backtick]afl[backtick]`: use `@@` or `@@@` to loop
- `iaito`: use the GUI "iaito"
- `config`: configure pretty much everything
- `r2 -e cfg.fortunes.tts=true`: have fortunes spoken to you
- `vim cmdlist.txt && r2 -i ./cmdlist.txt path/to/binary`: pass in pre defined list of commands
- `r2 -w path/to/binary`: permanently patch a binary with -w
- `ic`: list objective c classes and methods
- `~...`: interactive filter (real time) a command output with `...` after the `~` operator
- `randiff2`: use one of many cli tools that come with Radare2 to diff two binaries
- `r2 apk://[app loaction]`: analyse an android app using `apk://` prefix 
- `ic`: list android java classes and methods
- `i`: check compiler security features are used 
- `emulate`: emulate code (bunch of different commands)
- `roms`: analyse gameboy roms

## Further Reading

* [A Radare2 Tutorial series](https://www.youtube.com/playlist?list=PLg_QXA4bGHpvsW-qeoi3_yhiZg8zBzNwQ) - by BinaryAdventure on YouTube
* [Open Source Reverse Engineering: 60 Things In 60 Minutes](https://www.youtube.com/watch?v=7l67hP23OIE) - A talk about Radare2 given at our very own SecuriTay X by the wonderful Grant Douglas
* [The Github Repo](https://github.com/radareorg/radare2) - Keep up to date with (or even contribute to) Radare2 here
* [The Radare2 Book](https://book.rada.re/index.html) - As much documentation as your heart desires