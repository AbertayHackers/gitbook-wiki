# Project topic suggestions

This page will list some suggested topics for possible projects ranging from simple to expert. If you have any suggested topics, submit a pull request to [Github](https://github.com/AbertayHackers/) ([How to](https://wiki.hacksoc.co.uk/contributing/contributions/how-to))

## Offensive topics

- Malware infection vectors
- Evaluation of penetration tools
- OSINT techniques
- Exploit development
  - Ask Colin for a vulnerable program, or find your own!
  - Bypassing stack canaries, ASLR and CFG/CFI
- IOT hacking
- Social engineering/Spear phishing
- Layer 2 or 3 attacks
- Evaluation of an exploit eg Dirtyc0w

## Defensive topics

- Configuration of Splunk, or something like it
- Build, configure and evaluare GRSec or SELinux
- Hardening guide for a particular OS
- Something IDS related
- Read blue team field manual and do something from that

## Privacy topics

- Set up and configure TOR
- Comparison of encrypted messengers
- Evaluation of Protonmail and encrypted email clients
- Setting up, using and deploying PGP

## Other topics

- Evaluate a network protocol
- Set up and evaluate something like Pi-Hole, or something like that
- Evaluate a tool you use personally eg Little Flocker or Little Snitch on Mac

## OS Specific Research

### macOS

- Find and document Living off the Land Binaries (LOLBINS)
- Evaluate post exploit frameworks (Apfell, macshell/ macshellswift)
  - How you would prevent/ detect them?
- Write your own post exploit framework (do it in swift for bonus points and future proofing)
- Offensive Swift: How can you use/abuse swift to do bad stuff (You can execute Swift in a REPL and use it as a scripting language)
- Offensive JavaScript for Automation (JXA) what bad shit can you do with JXA how would you detect it?
- Offensive Apple Script (osascript) what bad shit can you do and how would you detect it?
- Really investigate macOS hardening
  - What can we do at the kernel level? (`kern.securelevel`)
    - [macOS and *OS Internals Vol3 Appendix A](http://newosxbook.com/files/moxii3/AppendixA.pdf)
  - MDM profile?
- Review Patrick Wardles ["The Mac Malware of 2019"](https://objective-see.com/blog/blog_0x53.html)
  - Extract common TTPs
    - How do they work?
    - How can we detect/ prevent them?
- [Forensics] Extend APOLLO by Sarah Edwards with more Mac feature
- Analyse installers (`.pkg`)s and find vulns
  - [hint](https://github.com/0xmachos/macos-scripts/commit/73403ff990164226ebe62c65977531e72af3e9bb#diff-3892527f3db79426cba00903ece969ab)
- Write a tool to automate macOS malware analysis
  - [MARA](https://github.com/xtiankisutsa/MARA_Framework) for mach-o?
- Write malware analysis tool based on the end point security framework
  - [hint](https://posts.specterops.io/detection-engineering-using-apples-endpoint-security-framework-affdbcb18b02)
  - [hint](https://www.jamf.com/blog/apples-new-endpoint-security-framework/)

### iOS

- How can you lock down iOS with MDM? (Micro MDM)
- Can you better monitor iOS with MDM?
- What logs can you get and how can you monitor these for exploitation?
- [Forensics] Play with APOLLO by Sarah Edwards evaluate it see if you can extend it?
- Jailbreak an iPhone and play with frida

These projects are perfect to do for your personal projects in 2nd and 3rd year, as well as talks at society. If you need help, ask!
